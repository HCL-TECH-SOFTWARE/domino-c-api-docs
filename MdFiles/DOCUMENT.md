




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



**DOCUMENT** **-** Document
Billing Record


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**



typedef struct {  

   WORD     Type;           

   TIMEDATE ReplicaID;      

   char     Username[MAXUSERNAME+1];  

   OID      OriginatorID;  

   NUMBER   Charge;  

} DOCUMENT;


 


**Description :**



To create
Document billing records, you must include the Document keyword in the
notes.ini BillingClass variable on the billing server. This enables the Lotus
Domino Server to write document-related information to the billing message
queue which then can be read into the DOCUMENT structure by a Domino billing
add-in server task.


 


When a
document contains a $ChargeRead hidden field, the server writes a Document
billing record to the message queue on a NSFNoteOpen.  If the document contains
a $ChargeWrite hidden field, the server writes a billing record to the message
queue on a NSFNoteUpdate.  This feature provides a mechanism for third party
information providers to charge for access to documents.


 


To insert
hidden charge fields in a form, see the *Domino Administration Help* database.


 


 


**Structure
Description**



**Type**:  Valid
values are BILLCHARGEREAD or BILLCHARGEWRITE.


 


**ReplicaID**:  Unique
identifier (ID) of the open database.


 


**Username**: 
Authenticated name of the user accessing the document.


 


**Originator
ID**:  The Originator ID (OID) of the note, used to report the
Universal Note ID (UNID).


 


**Charge**:  Cost
value of the $ChargeRead or $ChargeWrite field.


 **See Also :**


**[AGENTREC](AGENTREC.md)**


**[BILLCHARGExxx](BILLCHARGExxx.md)**


**[BILLMSG](BILLMSG.md)**


**[BILLREC](BILLREC.md)**


**[DBREC](DBREC.md)**


**[HTTPREQREC](HTTPREQREC.md)**


**[MAILREC](MAILREC.md)**


**[REPLREC](REPLREC.md)**


**[SESSIONREC](SESSIONREC.md)**



----------------------------------------------------------------------------------------------------------


 





