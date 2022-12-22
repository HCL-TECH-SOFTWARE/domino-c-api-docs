




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Function : Mail Gateway**



**MailAddRecipientsItem** **- Adds a
Recipients item to an open message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailAddRecipientsItem(**  

      DHANDLE  hMessage,  

      DHANDLE  hRecipientsItem,  

      WORD  RecipientsLength**);**



**Description :**



This
function adds a Recipients item to an open message.  This function is usually
used by gateways for creating inbound messages from foreign mail systems.  

  

The Recipients item consists of a text list of the full mail addresses of all
the recipients.  The Domino Mail Router requires a Recipients item to deliver
the message.   

  

Use the text list manipulation functions (ListAllocate, etc.) to create and
initialize the recipients item text list.  Use MailLookupAddress to look up the
full mail address for each recipient, then add each valid address to the list
before calling MailAddRecipientsItem. The text list item must have a
TYPE\_TEXT\_LIST data type prefix word, so specify prefix\_flag = TRUE in
ListAllocate and subsequent List functions.  MailAddRecipientsItem does not
copy the text list but transfers ownership of the memory associated with the
text list to the message itself.  Unlock the memory associated with the text
list but do not free the memory.  The memory will be freed by MailCloseMessage.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

hRecipientsItem  -  Recipients text list item handle.  

  

RecipientsLength  -  Recipients text list item size.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **Sample Usage :**


error = ListAllocate(0,
0, TRUE, &hRecipientsItem, &RecipientsItem,   

                    &RecipientsItemSize);  

if (error) goto Close;  

OSUnlockObject(hRecipientsItem);  

  

while (fgets(String, sizeof(String), ForeignFile))  

{  

    Code = String[0];  

    Value = &String[1];  

    ValueLength = strlen(Value);  

  

    error = ListAddEntry(hRecipientsItem, TRUE,   

            &RecipientsItemSize, Recipients,   

            Value, ValueLength);  

}  

error = MailAddRecipientsItem(hMessage, hRecipientsItem, RecipientsItemSize);  

if (error) goto Close;  

hRecipientsItem = NULLHANDLE;


 **See Also :**


**[ListAllocate](ListAllocate.md)**


**[ListAddEntry](ListAddEntry.md)**


**[MailLookupAddress](MailLookupAddress.md)**



----------------------------------------------------------------------------------------------------------


 





