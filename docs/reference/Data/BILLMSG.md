##### Data Type : Billing
##### BILLMSG - Billing Message
---
```
#include <billing.h>
```
**Description :**

Each billing record is prefaced by a header that contains common information 
about that billing record.  This information and the billing record, itself, 
comprise the Billing Message and  is stored by the BILLMSG data structure. 


Structure Description

Len -- Size of the BILLMSG structure

StructType -- Structure type of the billing record.  The defined values (see 
BILL_xxx (structure types)) are:

BILL_SESSIONREC  - Session billing record 
BILL_REPLREC - Replication billing record
BILL_DOCCHARGE - Document billing record
BILL_MAILREC - Mail billing record 
BILL_DBREC - Database billing record
BILL_AGENTREC - Agent billing record
BILL_HTTPREQREC - HTTP request billing record

These reserved literal values fall within the range of 1-32,000.   Custom or 
user-defined structure type values must be within the range of 32001-65535. 

Class -- Billing class of the billing record.  The supported values (see 
BILL_CLASS_xxx) are:

BILL_CLASS_SESSION
BILL_CLASS_REPLICATION
BILL_CLASS_DOCUMENT
BILL_CLASS_MAIL
BILL_CLASS_DATABASE
BILL_CLASS_AGENT
BILL_CLASS_HTTPREQUEST

ServerName -- Name of the Advanced Server that generated the billing record

TimeStamp -- Time when the billing record was written to the message queue

Rec -- Billing record structure that contains information about the specified 
StructType record

**See Also :**
[BillingWrite](/reference/Func/BillingWrite)
[BILLREC](/reference/Data/BILLREC)
[BILL_CLASS_xxx](/reference/Symb/BILL_CLASS_xxx)
[BILL_xxx (structure types)](/reference/Symb/BILL_xxx (structure types))
---
