##### Function : Access Control List
##### ACLSetFlags - Set flags that apply to the entire ACL
---
```
#include <acl.h>
STATUS LNPUBLIC ACLSetFlags(

	DHANDLE  hACL,
	DWORD  Flags);
```
**Description :**

Store new settings for flags that apply to the ACL itself.

**Parameters :**
Input :
hACL  -  Handle of the ACL.

Flags  -  New flag settings.

Output :
(routine)  -  NOERROR - Successfully stored new flags
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[ACLGetFlags](/domino-c-api-docs/reference/Func/ACLGetFlags)
[ACL_xxx](/domino-c-api-docs/reference/Symb/ACL_xxx)
---
