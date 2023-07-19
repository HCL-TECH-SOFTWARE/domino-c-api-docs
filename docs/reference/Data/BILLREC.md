##### Data Type : Billing
##### BILLREC - Billing Record
---
```
#include <billing.h>
```

**Definition :**

typedef union {
   SESSIONREC sess;
   REPLREC    repl;
   DOCUMENT   doc;
   MAILREC    mail;
   DBREC      db;
   AGENTREC   agent;
   HTTPREQREC HttpRequest;
} BILLREC;

**Description :**

The billing record contains billing information specific to the structure type ( BILL_xxx) defined in the billing message.   You can extend the billing record to include user-defined billing record structure types.
<ul><br>
<br>
<br>
<b><u>Structure Description</u></b><br>
<br>
<b>sess</b> -- Session billing record specified by BILL_SESSIONREC<br>
<br>
<b>repl -- </b>Replication billing record specified by BILL_REPLREC<br>
<br>
<b>doc -- </b>Document billing record specified by BILL_DOCCHARGE<br>
<br>
<b>mail</b> --  Mail billing record specified by BILL_MAILREC<br>
<br>
<b>db --</b> Database access billing record, specified by BILL_DBREC<br>
<br>
<b>agent -- </b>Agent billing record specified by BILL_AGENTREC<br>
<br>
<b>HttpRequest</b> --  Http request billing record specified by BILL_HTTPREQREC</ul>



**See Also :**
[AGENTREC](/domino-c-api-docs/reference/Data/AGENTREC)
[BillingWrite](/domino-c-api-docs/reference/Func/BillingWrite)
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
[DBREC](/domino-c-api-docs/reference/Data/DBREC)
[DOCUMENT](/domino-c-api-docs/reference/Data/DOCUMENT)
[HTTPREQREC](/domino-c-api-docs/reference/Data/HTTPREQREC)
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
[REPLREC](/domino-c-api-docs/reference/Data/REPLREC)
[SESSIONREC](/domino-c-api-docs/reference/Data/SESSIONREC)
---
