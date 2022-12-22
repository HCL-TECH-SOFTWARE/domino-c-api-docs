




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




 


**Symbolic Value : Mail Gateway**



**MAIL\_MESSAGE\_xxx** **-** Type of
message.


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**


 **Symbolic Values :**      MAIL\_MESSAGE\_UNKNOWN           -  The message is not one of
the types listed below and therefore is "unknown".  

  

      MAIL\_MESSAGE\_MEMO      -  The message is a normal memo/reply or any other
type of form.  

  

      MAIL\_MESSAGE\_DELIVERYREPORT          -  The message is a successful
delivery report.  

  

      MAIL\_MESSAGE\_NONDELIVERYREPORT   -  The message is an unsuccessful
delivery report.  

  

      MAIL\_MESSAGE\_RETURNRECEIPT            -  The message is a return receipt.  

  

      MAIL\_MESSAGE\_PHONEMESSAGE            -  The message is a phone message.  

  

      MAIL\_MESSAGE\_TRACEREPORT   -  The message is a trace delivery report.  

  

      MAIL\_MESSAGE\_NOTICE   -  The message is a calendar and scheduling notice,
such as an invitation or a confirmation.  

  

      MAIL\_MESSAGE\_QUOTAREPORT   -  This message is a quota report.  

  




**Description :**



Each
symbolic constant defines one of the well-known message types:  Memo (or
Reply), Delivery Report, NonDelivery Report, Return Receipt, PhoneMessage.


 **See Also :**


**[MailGetMessageType](MailGetMessageType.md)**



----------------------------------------------------------------------------------------------------------


 





