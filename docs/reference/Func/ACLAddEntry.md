##### Function : Access Control List
##### ACLAddEntry - Adds an entry to an access control list.
---
```
#include <acl.h>
STATUS LNPUBLIC ACLAddEntry(

	DHANDLE  hACL,
	const char far *Name,
	WORD  AccessLevel,
	ACL_PRIVILEGES far *Privileges,
	WORD  AccessFlags);
```
**Description :**

This function adds an entry to an access control list.

**Parameters :**
Input :
hACL  -  Handle to an access control list.

Name  -  Null-terminated string pointer to user or group to be added.  If you need to specify a hierarchical user name, be sure to use the fully distinguished name.

AccessLevel  -  Access level, ACL_LEVEL_xxx, of the entry to be added.  See Symbolic Value, ACL_LEVEL.

Privileges  -  Pointer to privilege bit mask of the entry to be added.  Use this parameter to assign roles to the entry.  See Data Type, ACL_PRIVILEGES.  See Data Type, ACL_PRIVILEGES.

AccessFlags  -  Access level modifier flags, ACL_FLAG_xxx  (eg:  unable to delete documents, unable to create documents), of the entry to be added.

Output :
(routine)  -  Return status from this call - indicates either success (NOERROR), or what the error is.



**See Also :**
[ACL_LEVEL_xxx](/domino-c-api-docs/reference/Symb/ACL_LEVEL_xxx)
[ACL_PRIVILEGES](/domino-c-api-docs/reference/Data/ACL_PRIVILEGES)
[ACL_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACL_FLAG_xxx)
[ACLCreate](/domino-c-api-docs/reference/Func/ACLCreate)
[ACLDeleteEntry](/domino-c-api-docs/reference/Func/ACLDeleteEntry)
---
