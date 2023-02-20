##### Function : Calendaring and Scheduling
##### SchContainer_FreeRequest - Free a request
---
```
#include <schgtw.h>
STATUS LNPUBLIC SchContainer_FreeRequest(

	DHANDLE  hCntnr,
	HCNTNROBJ  hRqst);
```
**Description :**

This routine is used to free a request. Requests are used to obtain free time 
information from a foreign system calendaring and scheduling gateway.

**Parameters :**
Input :
hCntnr  -  The container handle.

hRqst  -  Pointer to the object to free.

Output :
(routine)  -  NOERROR - Successfully freed a request.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.




**See Also :**
[SchContainer_GetRequest](/reference/Func/SchContainer_GetRequest)
---
