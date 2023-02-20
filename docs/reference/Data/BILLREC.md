##### Data Type : Billing
##### BILLREC - Billing Record
---
```
#include <billing.h>
```
**Description :**

The billing record contains billing information specific to the structure type 
( BILL_xxx) defined in the billing message.   You can extend the billing record 
to include user-defined billing record structure types.


Structure Description

sess -- Session billing record specified by BILL_SESSIONREC

repl -- Replication billing record specified by BILL_REPLREC

doc -- Document billing record specified by BILL_DOCCHARGE

mail --  Mail billing record specified by BILL_MAILREC

db -- Database access billing record, specified by BILL_DBREC

agent -- Agent billing record specified by BILL_AGENTREC

HttpRequest --  Http request billing record specified by BILL_HTTPREQREC

**See Also :**
[AGENTREC](/reference/Data/AGENTREC)
[BillingWrite](/reference/Func/BillingWrite)
[BILLMSG](/reference/Data/BILLMSG)
[DBREC](/reference/Data/DBREC)
[DOCUMENT](/reference/Data/DOCUMENT)
[HTTPREQREC](/reference/Data/HTTPREQREC)
[MAILREC](/reference/Data/MAILREC)
[REPLREC](/reference/Data/REPLREC)
[SESSIONREC](/reference/Data/SESSIONREC)
---
