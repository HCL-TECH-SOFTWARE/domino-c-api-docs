##### Symbolic Value : Billing
##### BILL_xxx (structure types) - Billing Record Structure Types
---
```
#include <billing.h>
```

**Symbolic Values :**

	BILL_SESSIONREC	  -  Session record structure type

	BILL_REPLREC	  -  Replication record structure type

	BILL_DOCCHARGE	  -  Document Charge record structure type

	BILL_MAILREC	  -  Mail record structure type

	BILL_DBREC	  -  Database record structure type

	BILL_AGENTREC	  -  Agent record structure type

	BILL_HTTPREQREC	  -  Http request record structure type


**Description :**

These constants provide values for the available Billing record structure types.  The Lotus Domino Server assigns these values to the StructType field of the BILLMSG billing message record.   Custom structure type constants, used by the BillingWrite() function, must be assigned values between the range of 32001 and 65535.


**See Also :**
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
---
