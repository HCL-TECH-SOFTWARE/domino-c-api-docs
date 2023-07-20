##### Symbolic Value : Billing
##### BILL_CLASS_xxx - Billing Classes
---
```
#include <billing.h>
```

**Symbolic Values :**

	BILL_CLASS_SESSION	  -  Session billing class

	BILL_CLASS_REPLICATION	  -  Replication billing class

	BILL_CLASS_DOCUMENT	  -  Document billing class

	BILL_CLASS_MAIL	  -  Mail billing class

	BILL_CLASS_DATABASE	  -  Database billing class

	BILL_CLASS_AGENT	  -  Agent billing class

	BILL_CLASS_HTTPREQUEST	  -  Http Request billing class


**Description :**

The above constants provide unique billing class values.   They can be bitwise OR'ed with a billing class mask, as returned by the BillingGetClass() function, to determine the active classes on the billing server.


**See Also :**
[BillingGetClass](/domino-c-api-docs/reference/Func/BillingGetClass)
---
