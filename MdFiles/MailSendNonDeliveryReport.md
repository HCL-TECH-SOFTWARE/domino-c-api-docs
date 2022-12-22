




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



**MailSendNonDeliveryReport** **- Sends a
Non-Delivery Report back to a message's originator.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailSendNonDeliveryReport(**  

      DARRAY far \*MessageList,  

      WORD  Message,  

      WORD  RecipientNums,  

      WORD far \*RecipientNumList,  

      char far \*ReasonText,  

      WORD  ReasonTextLength**);**



**Description :**



This
function sends a Non-Delivery Report back to a message's originator.  The
report can name one or more message recipients.  A gateway should send a
Non-Delivery Report when it encounters an unrecoverable failure attempting to
transfer or deliver the message to the recipients.  

  

The report includes a list of the recipients that were undeliverable, text
describing the failure, and all the original fields in the message.


 


**Parameters :**



Input :  

MessageList  -  Message list pointer.  

  

Message  -  Message number (0-n).  

  

RecipientNums  -  Count of recipient numbers in RecipientNumList.  

  

RecipientNumList  -  Pointer to an array of recipient numbers indicating the
undeliverable recipients.  

  

ReasonText  -  Reason text string pointer.  

  

ReasonTextLength  -  Reason text string length.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[MailSendDeliveryReport](MailSendDeliveryReport.md)**



----------------------------------------------------------------------------------------------------------


 





