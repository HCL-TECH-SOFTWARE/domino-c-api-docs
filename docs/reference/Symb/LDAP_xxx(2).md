##### Symbolic Value : LDAP
##### LDAP_xxx(2) - Possible error codes that can be returned.  (Continued)
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_OTHER	  -  Other.

	LDAP_SERVER_DOWN	  -  Server is down.

	LDAP_LOCAL_ERROR	  -  Local error.

	LDAP_ENCODING_ERROR	  -  Encoding error.

	LDAP_DECODING_ERROR	  -  Decoding error.

	LDAP_TIMEOUT	  -  Timeout.

	LDAP_AUTH_UNKNOWN	  -  Auth unknown.

	LDAP_FILTER_ERROR	  -  Filter error.

	LDAP_USER_CANCELLED	  -  User has cancelled operation.

	LDAP_PARAM_ERROR	  -  Parameter error.

	LDAP_NO_MEMORY	  -  No memory.

	LDAP_CONNECT_ERROR	  -  Connect error.

	LDAP_NOT_SUPPORTED	  -  Not supported.

	LDAP_CONTROL_NOT_FOUND	  -  Not found.

	LDAP_NO_RESULTS_RETURNED	  -  No results returned.

	LDAP_MORE_RESULTS_TO_RETURN	  -  More results to return.

	LDAP_CLIENT_LOOP	  -  Client loop.

	LDAP_REFERRAL_LIMIT_EXCEEDED	  -  Referral limit exceeded.

	LDAP_WILDCARD_MINIMUM_ERROR	  -  Wildcard minimum error.


**Description :**

Many of the LDAP API routines return result codes, some of which indicate local API errors and some of which are LDAP resultCodes that are returned by servers.  All of the result codes are non-negative integers.


**See Also :**
---
