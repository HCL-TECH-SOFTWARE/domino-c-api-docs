##### Function : Access Control List
##### ACLGetPrivName - Given a privilege number, get the privilege name.
---
```
#include <acl.h>
STATUS LNPUBLIC ACLGetPrivName(

	DHANDLE  hACL,
	WORD  PrivNum,
	char far *retPrivName);
```
**Description :**

This function returns the privilege name (role) associated with a given  
privilege number (0 through ACL_PRIVCOUNT - 1).  Privilege names associated 
with privilege numbers 0 through 4 are privilege levels compatible with 
versions of Notes prior to Release 3 and are enclosed in parenthesis.  
Privilege names associated with privilege numbers 5 through ACL_PRIVCOUNT - 1 
are members of the access role list and are enclosed in brackets.

**Parameters :**
Input :
hACL  -  Handle to an access control list.

PrivNum  -  Privilege number (0 through ACL_PRIVCOUNT - 1).

Output :
(routine)  -  Return status from this call - indicates either success (NOERROR), or what the error is.


retPrivName  -  Pointer to returned privilege or role name.  The buffer that holds the privilege or role name must be at least ACL_PRIVSTRINGMAX in size.


**See Also :**
[ACLSetPrivName](/domino-c-api-docs/reference/Func/ACLSetPrivName)
---
