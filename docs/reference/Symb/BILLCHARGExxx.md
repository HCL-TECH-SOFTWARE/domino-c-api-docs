##### Symbolic Value : Billing
##### BILLCHARGExxx - Document Billing type
---
```
#include <billing.h>
```

**Symbolic Values :**

	BILLCHARGEREAD	  -  Indicates the billing server accessed a $ChargeRead field in a document.

	BILLCHARGEWRITE	  -  Indicates the billing server accessed a $ChargeWrite field in a document.


**Description :**

These two constants identify the type of document operation that generated the billing record.  They are assigned to the Type parameter of the DOCUMENT billing record.<br>
<br>
	For more information, see the <i>Domino 5 Administration Help </i>documentation.


**See Also :**
[BillingWrite](/domino-c-api-docs/reference/Func/BillingWrite)
[DOCUMENT](/domino-c-api-docs/reference/Data/DOCUMENT)
---
