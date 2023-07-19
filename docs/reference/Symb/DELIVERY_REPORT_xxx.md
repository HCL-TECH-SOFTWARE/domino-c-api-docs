##### Symbolic Value : Mail Gateway
##### DELIVERY_REPORT_xxx - Type of delivery reporting option requested.
---
```
#include <mailserv.h>
```

**Symbolic Values :**

	DELIVERY_REPORT_NONE	  -  No report requested.

	DELIVERY_REPORT_BASIC	  -  Basic report (only on failure report) option requested. Report is sent only if the message could not be delivered.

	DELIVERY_REPORT_CONFIRMED	  -  Confirmation report option requested (notify sender that the message was or was not delivered).

	DELIVERY_REPORT_TRACE	  -  Trace entire path delivery option requested. A report is sent from each server the message is routed through. The final report indicates whether Domino delivered the message successfully.

	DELIVERY_REPORT_TRACE_NO_DELIVER	  -  Trace a delivery failure.

	DELIVERY_REPORT_CONFIRM_NO_DELIVER	  -  Confirm a delivery failure.


**Description :**

These symbolic constants define the type of delivery reporting option requested.  Used in MailGetMessageInfo function and MAILREC structure.


**See Also :**
[MailGetMessageInfo](/domino-c-api-docs/reference/Func/MailGetMessageInfo)
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
---
