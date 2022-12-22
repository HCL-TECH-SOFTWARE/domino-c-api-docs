




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




**Initial Release 4.0**



**Data Type : Billing**



**BILLREC** **-** Billing
Record


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**



typedef union {  

   SESSIONREC sess;  

   REPLREC    repl;  

   DOCUMENT   doc;  

   MAILREC    mail;


   DBREC      db;  

   AGENTREC   agent;


   HTTPREQREC
HttpRequest;


} BILLREC;


 


**Description :**



The billing
record contains billing information specific to the structure type ( BILL\_xxx)
defined in the billing message.   You can extend the billing record to include
user-defined billing record structure types.


 


 


**Structure
Description**



**sess** -- Session billing
record specified by BILL\_SESSIONREC


 


**repl --** Replication
billing record specified by BILL\_REPLREC


 


**doc --** Document
billing record specified by BILL\_DOCCHARGE


 


**mail** --  Mail
billing record specified by BILL\_MAILREC


 


**db --** Database
access billing record, specified by BILL\_DBREC


 


**agent --** Agent
billing record specified by BILL\_AGENTREC


 


**HttpRequest** --  Http
request billing record specified by BILL\_HTTPREQREC


 **See Also :**


**[AGENTREC](AGENTREC.md)**


**[BillingWrite](BillingWrite.md)**


**[BILLMSG](BILLMSG.md)**


**[DBREC](DBREC.md)**


**[DOCUMENT](DOCUMENT.md)**


**[HTTPREQREC](HTTPREQREC.md)**


**[MAILREC](MAILREC.md)**


**[REPLREC](REPLREC.md)**


**[SESSIONREC](SESSIONREC.md)**



----------------------------------------------------------------------------------------------------------


 





