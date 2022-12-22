




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



**BILLMSG** **-** Billing
Message


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**




typedef struct {  

   WORD     Len;        


   WORD     StructType;
  

   DWORD    Class;      


   char     ServerName[MAXUSERNAME+1];  

   TIMEDATE TimeStamp;  

   BILLREC  rec;  

} BILLMSG;


 


**Description :**



Each billing
record is prefaced by a header that contains common information about that
billing record.  This information and the billing record, itself, comprise the
Billing Message and  is stored by the BILLMSG data structure.   

  




 


**Structure
Description**



**Len** -- Size of
the BILLMSG structure


 


**StructType** --
Structure type of the billing record.  The defined values (see BILL\_xxx
(structure types)) are:


 


BILL\_SESSIONREC 
- Session billing record 


BILL\_REPLREC
- Replication billing record


BILL\_DOCCHARGE
- Document billing record


BILL\_MAILREC
- Mail billing record 


BILL\_DBREC -
Database billing record


BILL\_AGENTREC
- Agent billing record


BILL\_HTTPREQREC
- HTTP request billing record


 


These
reserved literal values fall within the range of 1-32,000.   Custom or
user-defined structure type values must be within the range of 32001-65535. 


 


**Class** -- Billing
class of the billing record.  The supported values (see BILL\_CLASS\_xxx) are:


 


BILL\_CLASS\_SESSION


BILL\_CLASS\_REPLICATION


BILL\_CLASS\_DOCUMENT


BILL\_CLASS\_MAIL


BILL\_CLASS\_DATABASE


BILL\_CLASS\_AGENT


BILL\_CLASS\_HTTPREQUEST


 


**ServerName** -- Name of
the Advanced Server that generated the billing record


 


**TimeStamp** -- Time
when the billing record was written to the message queue


 


**Rec** -- Billing record structure that contains information about the
specified StructType record


 **See Also :**


**[BillingWrite](BillingWrite.md)**


**[BILLREC](BILLREC.md)**


**[BILL\_CLASS\_xxx](BILL_CLASS_xxx.md)**


**[BILL\_xxx (structure types)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6756553F227FD375852563010073FD6A)**



----------------------------------------------------------------------------------------------------------


 





