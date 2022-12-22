




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



**MailGetMessageType** **- Returns
the type of an open message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



WORD
LNPUBLIC **MailGetMessageType(**  

      DHANDLE  hMessage**);**



**Description :**



This
function returns the type of an open message.  This function determines if the
message is one of the well-known message types:  Memo (or Reply), Delivery
Report, NonDelivery Report, Return Receipt, PhoneMessage.  

  

If the message is not one of the above, then the message type is
"unknown".  This function uses the Form field to determine the
message type.


 


**Parameters :**



Input :  

hMessage  -  Open message handle  

  




Output :  

(routine)  -  Type of message, which can be one of MAIL\_MESSAGE\_xxx.  

  

  




 **See Also :**


**[MAIL\_MESSAGE\_xxx](MAIL_MESSAGE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





