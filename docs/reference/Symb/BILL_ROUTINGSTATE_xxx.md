##### Symbolic Value : Billing
##### BILL_ROUTINGSTATE_xxx - MAILREC - RoutingState
---
```
#include <billing.h>
```

**Symbolic Values :**

	BILL_ROUTINGSTATE_PENDING	  -  Message is pending delivery.

	BILL_ROUTINGSTATE_DEAD	  -  Message is dead. ("DEAD")

	BILL_ROUTINGSTATE_HOLD	  -  Message is being held after non-delivery. ("HOLD")


**Description :**

The router adds an item (see MAIL_ROUTINGSTATE_ITEM_NUM) to non-deliverable messages.  The value of this item follows the description of each (non-delivery) symbol above.


**See Also :**
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
[MAIL_xxx_ITEM_NUM(1)](/domino-c-api-docs/reference/Symb/MAIL_xxx_ITEM_NUM(1))
---
