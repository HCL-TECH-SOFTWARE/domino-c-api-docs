




<!--
 /\* Font Definitions \*/
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



**MailPurgeMessage** **- Deletes
message from message file under certain conditions.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailPurgeMessage(**  

      DARRAY far \*MessageList,  

      WORD  Message**);**



**Description :**



This
function deletes a message from the message file if either:  1) all of the
recipients of the message have been deleted (via MailDeleteMessageRecipient)
or, 2) the message has not been transferred in a reasonable amount of time (the
"timeout" value).  

  

If all of the recipients have not been deleted from the message, the message is
re-saved in the message file, with only the undeleted recipients remaining. 
This allows a gateway to attempt to transfer the message to those recipients at
a later time.  

  

If a message has not been delivered within the timeout, the MailPurgeMessage
function sends a Non-Delivery Report to all remaining recipients.  The timeout
can be set on a per-server basis by setting the MailTimeout variable in
notes.ini to the number of hours.  The default is 24 hours.


 


**Parameters :**



Input :  

MessageList  -  Message list pointer.  

  

Message  -  Message number (0-n).  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[MailDeleteMessageRecipient](MailDeleteMessageRecipient.md)**



----------------------------------------------------------------------------------------------------------


 





