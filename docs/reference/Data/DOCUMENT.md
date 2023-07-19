##### Data Type : Billing
##### DOCUMENT - Document Billing Record
---
```
#include <billing.h>
```

**Definition :**

typedef struct {
   WORD     Type;         
   TIMEDATE ReplicaID;    
   char     Username[MAXUSERNAME+1];
   OID      OriginatorID;
   NUMBER   Charge;
} DOCUMENT;

**Description :**

To create Document billing records, you must include the Document keyword in the notes.ini BillingClass variable on the billing server. This enables the Lotus Domino Server to write document-related information to the billing message queue which then can be read into the DOCUMENT structure by a Domino billing add-in server task.
<ul><br>
<br>
When a document contains a $ChargeRead hidden field, the server writes a Document billing record to the message queue on a NSFNoteOpen.  If the document contains a $ChargeWrite hidden field, the server writes a billing record to the message queue on a NSFNoteUpdate.  This feature provides a mechanism for third party information providers to charge for access to documents.<br>
<br>
To insert hidden charge fields in a form, see the <i>Domino Administration Help </i>database.<br>
<br>
<br>
<b><u>Structure Description</u></b><br>
<br>
<b>Type</b>:  Valid values are BILLCHARGEREAD or BILLCHARGEWRITE.<br>
<br>
<b>ReplicaID</b>:  Unique identifier (ID) of the open database.<br>
<br>
<b>Username</b>:  Authenticated name of the user accessing the document.<br>
<br>
<b>Originator ID</b>:  The Originator ID (OID) of the note, used to report the Universal Note ID (UNID).<br>
<br>
<b>Charge</b>:  Cost value of the $ChargeRead or $ChargeWrite field.</ul>



**See Also :**
[AGENTREC](/domino-c-api-docs/reference/Data/AGENTREC)
[BILLCHARGExxx](/domino-c-api-docs/reference/Symb/BILLCHARGExxx)
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
[BILLREC](/domino-c-api-docs/reference/Data/BILLREC)
[DBREC](/domino-c-api-docs/reference/Data/DBREC)
[HTTPREQREC](/domino-c-api-docs/reference/Data/HTTPREQREC)
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
[REPLREC](/domino-c-api-docs/reference/Data/REPLREC)
[SESSIONREC](/domino-c-api-docs/reference/Data/SESSIONREC)
---
