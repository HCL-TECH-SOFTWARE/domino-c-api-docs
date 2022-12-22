




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



**MAILREC** **-** Mail Billing
Record


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**



typedef struct {  

   char     FormType[DESIGN\_NAME\_MAX]; /\* Type of Form \*/ 


   OID     
OriginatorID;              /\* Message Id \*/  

   UNID     OrigMessageID;             /\* $Ref if NonDelivery


                                         
Report \*/  

   DWORD    MessageSize;               /\* Size of message \*/  

   char     HopName[MAXUSERNAME+1];    /\* Next Server Name \*/  

   WORD     Priority;                  /\* Delivery priority \*/  

   WORD     RoutingState;              /\* see 


                                         
BILL\_ROUTINGSTATE\_xxx \*/  

   WORD     Report;                    /\* Delivery report


                                         
request \*/  

   char     Originator[MAXUSERNAME+1]; /\* From: \*/  

   WORD     RecipientCount;            /\* Recipients count \*/  

   WORD     RecipientSize;             /\* Recipients string size \*/  

   TIMEDATE PostedDate;                /\* Uniquely identify


                                         
instance of Mail


                                         
message \*/  

/\* Recipients char string immediately follows this structure \*/


} MAILREC;


 


**Description :**



To create
Mail billing records, you must include the Mail keyword in the notes.ini
BillingClass variable on the server.  This enables the server to generate a
Mail billing record for each message that the mail router processes which then
can be read into the MAILREC structure by a Domino billing add-in server task.


 


For more
information about billing for Domino mail activities, see the *Domino 5
Administration Help* database*.*



**Structure
Description**



**FormType**:  Type of
mail form.  Valid values are part of the C API, in stdnames.h, and include
MAIL\_MEMO\_FORM, MAIL\_REPLY\_FORM, MAIL\_PHONEMESSAGE\_FORM,
MAIL\_DELIVERYREPORT\_FORM, MAIL\_NONDELIVERYREPORTFORM, MAIL\_RETURNRECEIPT\_FORM,
and MAIL\_DATABASEENTRY\_FORM.


 


**OriginatorID**: 
Originator ID (OID) of the mail message, for reporting the Universal Note ID
(UNID).  The UNID of the mail message uniquely identifies a mail message. 
However if the message splits due to group expansion, error processing, or mail
forwarding addressing, a new field ($Orig) is added to the note.  The $Orig field
contains the original UNID of the mail message.  Since mail tries to preserve
the UNID of mail messages, the PostedDate value is needed to specify a
particular instance of a message being sent.


 


**OrigMessageID**:  The
unique mail identifier (UNID) of the original message.   This identifier is
used to maintain the original message ID when new message splits occur.  If
NULL, then the OriginatorID value is used to uniquely identify a mail message. 


 


**MessageSize**:  Total
size of the mail message, including header information, mail body, and any
attachments.


 


**HopName**:  Name of
the next server to which the mail message is being routed. When a message
routes through more than one server, this name changes to show the next server
to receive the message.


 


**Priority**:  Delivery
priority of the mail message. Values are Low, Normal, and High.


 


**Routing
State**:  See BILL\_ROUTINGSTATE\_xxx.


 


**Report**:  Delivery
report request of the mail message.


 


**Originator**:  Sender of
the mail message as specified in the From: field.


 


**RecipientCount**:  Number of
intended recipients of the mail message.


 


**RecipientSize**:  Size of
the recipient list string.


 


**PostedDate**:  Date and
time when the message was posted to the server mailbox.  This value, along with
the unique message ID, identify the mail billing instance.


 


 


**Notes****:**



The
recipient list string immediately follows the MAILREC structure.  It contains a
list of recipients, each name delimited by a comma. 


 


The
recipient count is used to determine the number of recipients to which the message
was delivered.  This allows for crediting of undelivered messages in case of
delivery errors.


 **See Also :**


**[AGENTREC](AGENTREC.md)**


**[BILLMSG](BILLMSG.md)**


**[BILLREC](BILLREC.md)**


**[BILL\_ROUTINGSTATE\_xxx](BILL_ROUTINGSTATE_xxx.md)**


**[DBREC](DBREC.md)**


**[DOCUMENT](DOCUMENT.md)**


**[HTTPREQREC](HTTPREQREC.md)**


**[REPLREC](REPLREC.md)**


**[SESSIONREC](SESSIONREC.md)**



----------------------------------------------------------------------------------------------------------


 





