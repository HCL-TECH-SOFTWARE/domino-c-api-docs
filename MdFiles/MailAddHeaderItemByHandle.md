




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



**MailAddHeaderItemByHandle** **- Adds a
header item to an open message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailAddHeaderItemByHandle(**  

      DHANDLE  hMessage,  

      WORD  ItemCode,  

      DHANDLE  hValue,  

      WORD  ValueLength,  

      WORD  ItemFlags**);**



**Description :**



This
function adds a header item to an open message.  Use this function to add items
if your program has a handle to the item value. If your program has a pointer
to the item value, use MailAddHeaderItem.  

  

Unlock the handle to the item value before calling this function. This function
transfers the memory specified by the handle to the message. If the function
returns successfully, do not free this memory.  

  

Use MailAddHeaderItemByHandle if your program has a handle to the item value,
particularly text lists created with ListAllocate. Use ListAllocate and
ListAddEntry to initialize the list. Unlock but do not free the list. Add the
list to the message by calling MailAddHeaderItemByHandle.
MailAddHeaderItemByHandle adds the list to the message efficiently because it
transfers ownership of the memory specified by the handle to the message. It
does not allocate additional memory for the item value, nor does it copy the
item value. Therefore, if MailAddHeaderItemByHandle succeeds, do not free the
memory specified by the handle.  

  

This function always sets the ITEM\_SUMMARY item flag, allowing the item to be
used in views and formulas.  However, if the value length is greater than 8KB,
NSF clears the ITEM\_SUMMARY flag.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

ItemCode  -  Item code; all of the MAIL\_xxx\_ITEM\_NUM item codes are valid.  

  

hValue  -  Item value handle.  

  

ValueLength  -  Item value length.  

  

ItemFlags  -  Optional NSF item flags (ITEM\_SIGN, ITEM\_SEAL).  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **Sample Usage :**


  

    if (error = ListAllocate(0, 0, TRUE, &hToItem, &ToItem,
&ToItemSize))  

    {  

        goto Close;  

    }  

    OSUnlockObject(hToItem);  

  

    for (/\* each SendTo name \*/)  

    {  

        error = ListAddEntry(hToItem, TRUE, &ToItemSize, ToEntries, Value,
ValueLength);  

        ToEntries++;  

    }  

             

    if (error = MailAddHeaderItemByHandle(hMessage, MAIL\_SENDTO\_ITEM\_NUM,
hToItem, ToItemSize, 0))  

    {  

        goto Close;  

    }  

    hToItem = NULLHANDLE;  

  




 **See Also :**


**[ListAddEntry](ListAddEntry.md)**


**[ListAllocate](ListAllocate.md)**


**[MailAddHeaderItem](MailAddHeaderItem.md)**


**[MAIL\_xxx\_ITEM\_NUM(1)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255CF1005E1A42)**


**[MAIL\_xxx\_ITEM\_NUM(2)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/9AB3CEDDDF02771B8525667A006D464F)**



----------------------------------------------------------------------------------------------------------


 





