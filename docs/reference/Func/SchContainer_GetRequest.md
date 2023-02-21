##### Function : Calendaring and Scheduling
##### SchContainer_GetRequest - Get the first request in a container.
---
```
#include <schgtw.h>
STATUS LNPUBLIC SchContainer_GetRequest(

	DHANDLE  hCntnr,
	HCNTNROBJ FAR *rethRqst,
	void FAR * FAR *retpRqst,
	LIST FAR * FAR *retpNameList,
	LIST FAR * FAR *repClientNames,
	char FAR * FAR *retpNS);
```
**Description :**

This function is used to get the first request in a container. Requests are 
used to obtain free time information from a foreign system calendaring and 
scheduling gateway.

**Parameters :**
Input :
hCntnr  -  The container Handle

Output :
(routine)  -  NOERROR - Successfully got the request.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



rethRqst  -  Points to where we return the handle to the request.

retpRqst  -  Points to where we return the pointer to the request.

retpNameList  -  Points to where we return the list of names to query.

repClientNames  -  Points to list of clients names doing the query.

retpNS  -  Points to name of Lotus Domino Server to chain to.


**See Also :**
[SchContainer_FreeRequest](/domino-c-api-docs/reference/Func/SchContainer_FreeRequest)
---
