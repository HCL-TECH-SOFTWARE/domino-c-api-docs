##### Data Type : Billing
##### BILLREC - Billing Record
---
##### #include <billing.h>
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
[AGENTREC](D:/md_files/AGENTREC.md)
[BillingWrite](D:/md_files/BillingWrite.md)
[BILLMSG](D:/md_files/BILLMSG.md)
[DBREC](D:/md_files/DBREC.md)
[DOCUMENT](D:/md_files/DOCUMENT.md)
[HTTPREQREC](D:/md_files/HTTPREQREC.md)
[MAILREC](D:/md_files/MAILREC.md)
[REPLREC](D:/md_files/REPLREC.md)
[SESSIONREC](D:/md_files/SESSIONREC.md)
---
