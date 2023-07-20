##### Data Type : Billing
##### BILLMSG - Billing Message
---
```
#include <billing.h>
```

**Definition :**
```
typedef struct {
   WORD     Len;        
   WORD     StructType; 
   DWORD    Class;      
   char     ServerName[MAXUSERNAME+1];
   TIMEDATE TimeStamp;
   BILLREC  rec;
} BILLMSG;
```

**Description :**

Each billing record is prefaced by a header that contains common information about that billing record.  This information and the billing record, itself, comprise the Billing Message and  is stored by the BILLMSG data structure. <br>

<ul><br>
<br>
<b><u>Structure Description</u></b><br>
<br>
<b>Len</b> -- Size of the BILLMSG structure<br>
<br>
<b>StructType</b> -- Structure type of the billing record.  The defined values (see BILL_xxx (structure types)) are:<br>
<br>
BILL_SESSIONREC  - Session billing record <br>
BILL_REPLREC - Replication billing record<br>
BILL_DOCCHARGE - Document billing record<br>
BILL_MAILREC - Mail billing record <br>
BILL_DBREC - Database billing record<br>
BILL_AGENTREC - Agent billing record<br>
BILL_HTTPREQREC - HTTP request billing record<br>
<br>
These reserved literal values fall within the range of 1-32,000.   Custom or user-defined structure type values must be within the range of 32001-65535. <br>
<br>
<b>Class</b> -- Billing class of the billing record.  The supported values (see BILL_CLASS_xxx) are:<br>
<br>
BILL_CLASS_SESSION<br>
BILL_CLASS_REPLICATION<br>
BILL_CLASS_DOCUMENT<br>
BILL_CLASS_MAIL<br>
BILL_CLASS_DATABASE<br>
BILL_CLASS_AGENT<br>
BILL_CLASS_HTTPREQUEST<br>
<br>
<b>ServerName </b>-- Name of the Advanced Server that generated the billing record<br>
<br>
<b>TimeStamp</b> -- Time when the billing record was written to the message queue</ul>
<br>
<b>Rec</b> -- Billing record structure that contains information about the specified StructType record


**See Also :**
[BillingWrite](/domino-c-api-docs/reference/Func/BillingWrite)
[BILLREC](/domino-c-api-docs/reference/Data/BILLREC)
[BILL_CLASS_xxx](/domino-c-api-docs/reference/Symb/BILL_CLASS_xxx)
[BILL_xxx (structure types)](/domino-c-api-docs/reference/Symb/BILL_xxx (structure types))
---
