




<!--
 /\* Font Definitions \*/
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



**Symbolic Value : Billing**



**BILL\_xxx (structure types)** **-** Billing
Record Structure Types


**----------------------------------------------------------------------------------------------------------**



**#include <billing.h>**


 **Symbolic Values :**      BILL\_SESSIONREC              -  Session record structure
type  

  

      BILL\_REPLREC        -  Replication record structure type  

  

      BILL\_DOCCHARGE              -  Document Charge record structure type  

  

      BILL\_MAILREC         -  Mail record structure type  

  

      BILL\_DBREC            -  Database record structure type  

  

      BILL\_AGENTREC     -  Agent record structure type  

  

      BILL\_HTTPREQREC            -  Http request record structure type  

  




**Description :**



These
constants provide values for the available Billing record structure types.  The
Lotus Domino Server assigns these values to the StructType field of the BILLMSG
billing message record.   Custom structure type constants, used by the
BillingWrite() function, must be assigned values between the range of 32001 and
65535.


 **See Also :**


**[BILLMSG](BILLMSG.md)**



----------------------------------------------------------------------------------------------------------


 





