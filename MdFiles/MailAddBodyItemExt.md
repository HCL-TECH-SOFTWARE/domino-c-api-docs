




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 5.0.7**



**Function : Mail Gateway**



**MailAddBodyItemExt** **- Adds an
in-memory text Body item to an open message, allowing use of NLS\_INFO
structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailAddBodyItemExt(**  

      DHANDLE  hMessage,  

      DHANDLE  hBodyItem,  

      DWORD  BodyLength,  

      NLS\_PINFO  pInfo**);**



**Description :**



This
function adds an in-memory text Body item to a message, allowing the use of the
NLS\_INFO structure.  Use this function with a text-only body item created by
MailCreateBodyItem and initialized by MailAppendBodyItemLine.  

  

Use MailAddBodyItem if your program reads text from a file or stream one line
at a time, and appends the text to a message body. Do not use this function if
the body will exceed 64K bytes.  For body items larger than 64K, see
MailAddMessageBodyText.  

  

MailAddBodyItem takes as input a handle to a plain text body item.  First call
MailCreateBodyItem to create the plain text body item. This yields the body
item handle, hBodyItem.  Then append one or more lines of text to the body item
by repeatedly calling MailAppendBodyItemLine. Pass the body item handle as
input to MailAppendBodyItemLine.  After processing all lines, call
MailAddBodyItem to add the body to the message.   

  

MailAddBodyItem converts the plain text specified by hBodyItem into rich text
and appends the rich text item to the message. After transferring the message
to the mail box and closing the message, call OSMemFree to free the memory
associated with the plain text body item handle, hBodyItem.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

hBodyItem  -  Body item handle.  

  

BodyLength  -  Body length.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  (NULL if body text already
in the Lotus Multibyte Character Set (LMBCS)).  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **Sample Usage :**


    STATUS error;   

    DHANDLE hMailboxFile, hMessage, hBodyItem;  

    DWORD BodySize;  

    char String[MAXFILELINELEN];  

  

    /\* Call MailOpenMessgeFile- this initializes hMailBoxFile \*/  

    /\* Call MailCreateMessage - this initializes hMessage \*/  

    /\* Open text input file \*/  

  

    error = MailCreateBodyItem(&hBodyItem, &BodySize);  

    if (error) goto done;  

  

    while (/\* still more text in input file /))  

    {  

        /\* get next line from input file into String[] \*/  

  

        error = MailAppendBodyItemLine(hBodyItem, &BodySize, String,
strlen(String));  

        if (error) break;  

    }  

  

    /\* close text input file \*/  

  

    error = MailAddBodyItemExt(hMessage, hBodyItem, BodySize, NULL);  

    if (error) goto Close;  

  

    /\* Transfer the message to the local mail router \*/  

Close:  

    MailCloseMessage(hMessage);  

    OSMemFree(hBodyItem);  

    /\* close message file \*/


 


 **See Also :**


**[MailAddMessageBodyTextExt](MailAddMessageBodyTextExt.md)**


**[MailAppendBodyItemLine](MailAppendBodyItemLine.md)**


**[MailCreateBodyItem](MailCreateBodyItem.md)**


**[OSMemFree](OSMemFree.md)**



----------------------------------------------------------------------------------------------------------


 





