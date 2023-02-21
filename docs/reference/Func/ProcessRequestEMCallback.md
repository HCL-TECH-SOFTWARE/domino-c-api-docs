##### Function : Extension Manager
##### ProcessRequestEMCallback - Extension Manager callback for EM_ADMINPPROCESSREQUEST,
---
```
#include <extmgr.h>
STATUS LNPUBLIC ProcessRequestEMCallback(

	NOTEHANDLE  nhRequest,
	NOTEHANDLE  nhResponse);
```
**Description :**

This callback enables you to extend the Administration Process.  For example, 
you can generate additional administration requests and store them in the 
Aministration Requests database.  

The EM_ADMINPPROCESSREQUEST occurs prior to and after the Administration 
Process has processed a request on a server.

Note:  Extensions to the Administration Process should not modify database ACLs 
because their actions could conflict with the Administration Process's standard 
ACL modification operations.

**Parameters :**
Input :
nhRequest  -  The handle of the Admin Request note.

nhResponse  -  The handle of the Admin Log note.  After the Administration Process performs the Administration Request, the "$AdminpNoErrorDbs" field of the AdminLog has a text list of the databases that were successfully processed by the request and the "$AdminpErrorDbs" field of the AdminLog has a text list of the databases that logged an error when the request was processed.

Output :
(routine)  -  
ERR_EM_CONTINUE



**See Also :**
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
---
