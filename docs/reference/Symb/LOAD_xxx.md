##### Symbolic Value : Mail Gateway
##### LOAD_xxx - MailLoadRoutingTablesExt - LoadFlags
---
```
#include <mailserv.h>
```

**Symbolic Values :**

	LOAD_INTERNALSMTP	  -  Support internal SMTP transfer thread and DNS.

	LOAD_EXTERNALSMTP	  -  Support SMTP transfer out of local domain.

	LOAD USEDNS	  -  Use DNS when resolving names.

	LOAD_USEHOSTS	  -  Use host's file when resolving names.

	LOAD_SERVERREACHABLE	  -  Need to be in same named network.

	LOAD_INTERNALSMTPALWAYS	  -  Support internal SMTP even for non MIME messages.

	LOAD_NOSERVERCACHE	  -  Disable server cache.

	LOAD_NODOMAINCACHE	  -  Disable domain cache.

	LOAD_NOFOREIGNSMTPDOMAINS	  -  Disable Foreign SMTP Domains when SMTP External is enabled.

	LOAD_NOSKIPDNSQUERY	  -  Do not skip the DNS query for domains without a ".".

	LOAD_ORDERCONNECTIONSBYDEST	  -  Order and search connections by destination domain/server name.

	LOAD_LIMITNRPCROUTING	  -  TRUE to limit routing algorithm to smtp external routing logic for internet domains.

	LOAD_COSTBIASDECISION	  -  TRUE to cause routing algorithm to use raw cost bias as an additional decision point


**Description :**

These symbols are optional load flags for MailLoadingRoutingTablesExt.


**See Also :**
[MailLoadRoutingTablesExt](/domino-c-api-docs/reference/Func/MailLoadRoutingTablesExt)
---
