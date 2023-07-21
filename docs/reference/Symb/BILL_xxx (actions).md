##### Symbolic Value : Billing
##### BILL_xxx (actions) - Session Billing Actions
---
```
#include <billing.h>
```

**Symbolic Values :**

	BILL_SESSION_START	  -  Indicates the first session record for this session

	BILL_DB_OPEN	  -  Indicates the database is open

	BILL_DB_CLOSE	  -  Indicates a request to close the database. This action enables Domino billing to track how often a database opens and closes during a session

	BILL_SESSION_STAMP	  -  Indicates the session is active. This stamp occurs if the timer specified by the notes.ini BillingSuppressTime variable expires and there is database activity only

	BILL_DB_STAMP	  -  Indicates the database activity during an open session

	BILL_DB_CLOSE_END	  -  Indicates the server closed the database when the session ended

	BILL_SESSION_END	  -  Indicates the session has ended


**Description :**

The above constants define the state of a Domino database or session at the time the billing record occurs. The values are assigned to the Action field of the SESSIONREC and DBREC billing records, as appropriate.  


**See Also :**
[DBREC](/domino-c-api-docs/reference/Data/DBREC)
[SESSIONREC](/domino-c-api-docs/reference/Data/SESSIONREC)
---
