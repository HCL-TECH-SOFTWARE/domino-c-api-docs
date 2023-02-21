##### Function : Access Control List
##### ACLEnumEntries - Enumerates an access control list's entries.
---
```
#include <acl.h>
STATUS LNPUBLIC ACLEnumEntries(

	DHANDLE  hACL,
	void LNCALLBACKPTR  EnumFunc,
	void far *EnumFuncParam);
```
**Description :**

This function enumerates the entries in an access control list.

**Parameters :**
Input :
hACL  -   Handle to an access control list.

EnumFunc  -  Far pointer to a user defined EnumFunc callback function.  This callback function is called with information about each entry in the list and is defined as:

      void (LNCALLBACKPTR EnumFunc)(
                              void far *EnumFuncParam,
                              char far *Name,
                              WORD AccessLevel,
                              ACL_PRIVILEGES far *Privileges,
                              WORD AccessFlags)

The EnumFuncParam argument is a pointer to data that has been passed to ACLEnumEntries to be used by EnumFunc.  The Name argument is the user name.  The AccessLevel argument is the access level (ACL_LEVEL_xxx).  The Privileges argument is a pointer to the privilege bit mask (see the Data Type, ACL_PRIVILEGES).  The AccessFlags argument is the access level modifier flags (ACL_FLAG_xxx).

The callback function cannot be used to modify the access control list.

EnumFuncParam  -  Pointer to data to be passed to EnumFunc.  This provides a way to pass non-global data to EnumFunc.

Output :
(routine)  -   Return status from this call - indicates either success (NOERROR), or what the error is.



**See Also :**
[ACL_PRIVILEGES](/domino-c-api-docs/reference/Data/ACL_PRIVILEGES)
[ACL_LEVEL_xxx](/domino-c-api-docs/reference/Symb/ACL_LEVEL_xxx)
[ACL_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACL_FLAG_xxx)
---
