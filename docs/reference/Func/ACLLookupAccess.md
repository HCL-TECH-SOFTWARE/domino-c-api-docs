##### Function : Access Control List
##### ACLLookupAccess - Returns ACL information for the specified names.
---
```
#include <acl.h>
STATUS LNPUBLIC ACLLookupAccess(

	DHANDLE  hACL,
	NAMES_LIST far *pNamesList,
	WORD far *retAccessLevel,
	ACL_PRIVILEGES far *retPrivileges,
	WORD far *retAccessFlags,
	DHANDLE far *rethPrivNames);
```
**Description :**

This function looks up all the specified names in the access control list and 
returns the maximum of the authorized level and privileges.  If none of the 
specified names are found in the list, the level and privileges for the default 
entry are returned.  If no names are supplied, then the level and privileges 
for the minimal entry are returned.

If the ACL contains multiple occurrences of a name, this function applies the 
same rules as the Notes User Interface when determining which access level 
takes precedence.  For example, if a user's name is included in the ACL, and 
that name is also a member of a group included in the ACL, then the explicit 
name will always take precedence--even if it has a lower access level than the 
group name.

**Parameters :**
Input :
hACL  -  Handle to an access control list.

pNamesList  -   Pointer to a NAMES_LIST structure.  The user name and then all group names that the user is a member of (directly or indirectly) must immediately follow the NAMES_LIST structure as contiguous null-terminated LMBCS strings.  If this pointer is NULL, then the access information of the entry with the minimum access is returned.  If the pointer is not NULL, then the NAMES_LIST must have at least a user name in it.  Otherwise, the default access is returned.  If you need to specify a hierarchical user name, be sure to use the fully distinguished name.

Output :
(routine)  -  Return status from this call - indicates either success (NOERROR), or what the error is.


retAccessLevel  -   Pointer to the returned access level, ACL_LEVEL_xxx.  See Symbolic Value, ACL_LEVEL.

retPrivileges  -  Pointer to returned privilege bit mask.  See Data Type, ACL_PRIVILEGES.

retAccessFlags  -  Pointer to returned access level modifier flags, ACL_FLAG_xxx  (eg:  unable to delete documents, unable to create documents).

rethPrivNames  -  Pointer to a handle to a text list which contains the privilege names or roles for that user.  Use OSLockObject to obtain a pointer to this text list.  ListGetText may then be used to get the entries in this text list.  After processing the text list, use OSUnlockObject to unlock the text list pointer and OSMemFree to free the memory associated with this handle.


**See Also :**
[ACL_LEVEL_xxx](/reference/Symb/ACL_LEVEL_xxx)
[ACL_PRIVILEGES](/reference/Data/ACL_PRIVILEGES)
[ACL_FLAG_xxx](/reference/Symb/ACL_FLAG_xxx)
[NAMES_LIST](/reference/Data/NAMES_LIST)
---
