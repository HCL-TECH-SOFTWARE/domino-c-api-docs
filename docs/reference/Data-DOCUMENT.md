##### Data Type : Billing
##### DOCUMENT - Document Billing Record
---
##### #include <billing.h>
**Description :**
To create Document billing records, you must include the Document keyword in 
the notes.ini BillingClass variable on the billing server. This enables the 
Lotus Domino Server to write document-related information to the billing 
message queue which then can be read into the DOCUMENT structure by a Domino 
billing add-in server task.

When a document contains a $ChargeRead hidden field, the server writes a 
Document billing record to the message queue on a NSFNoteOpen.  If the document 
contains a $ChargeWrite hidden field, the server writes a billing record to the 
message queue on a NSFNoteUpdate.  This feature provides a mechanism for third 
party information providers to charge for access to documents.

To insert hidden charge fields in a form, see the Domino Administration Help 
database.


Structure Description

Type:  Valid values are BILLCHARGEREAD or BILLCHARGEWRITE.

ReplicaID:  Unique identifier (ID) of the open database.

Username:  Authenticated name of the user accessing the document.

Originator ID:  The Originator ID (OID) of the note, used to report the 
Universal Note ID (UNID).

Charge:  Cost value of the $ChargeRead or $ChargeWrite field.
**See Also :**
[AGENTREC](D:/md_files/AGENTREC.md)
[BILLCHARGExxx](D:/md_files/BILLCHARGExxx.md)
[BILLMSG](D:/md_files/BILLMSG.md)
[BILLREC](D:/md_files/BILLREC.md)
[DBREC](D:/md_files/DBREC.md)
[HTTPREQREC](D:/md_files/HTTPREQREC.md)
[MAILREC](D:/md_files/MAILREC.md)
[REPLREC](D:/md_files/REPLREC.md)
[SESSIONREC](D:/md_files/SESSIONREC.md)
---
