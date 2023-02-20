##### Function : Calendaring and Scheduling
##### SchContainer_DupHandle - Duplicate the container handle.
---
```
#include <schgtw.h>
STATUS LNPUBLIC SchContainer_DupHandle(

	HCNTNR  hOrigCntnr,
	HCNTNR FAR *phDup);
```
**Description :**

This routine duplicates the handle to a container. The new container handle is 
valid in the context of the current process. This is used by gateways because 
they receive requests for schedules in a container. They use this call to 
instantiate the handle in the context of their process. This insures that 
Domino won't free the container memory until both processes release the handle 
by calling SchContainer_Free.

**Parameters :**
Input :
hOrigCntnr  -  The container handle to be duplicated.

Output :
(routine)  -  NOERROR - Successfully duplicated a container handle.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



phDup  -  Pointer to the newly duplicated container handle.


**See Also :**
[SchContainer_Free](/reference/Func/SchContainer_Free)
[SchContainer_New](/reference/Func/SchContainer_New)
[SchRetrieve](/reference/Func/SchRetrieve)
[SchSrvRetrieve](/reference/Func/SchSrvRetrieve)
---
