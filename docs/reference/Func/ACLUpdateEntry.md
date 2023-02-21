##### Function : Access Control List
##### ACLUpdateEntry - Updates an entry in an access control list.
---
```
#include <acl.h>
STATUS LNPUBLIC ACLUpdateEntry(

	DHANDLE  hACL,
	const char far *Name,
	WORD  UpdateFlags,
	const char far *NewName,
	WORD  NewAccessLevel,
	ACL_PRIVILEGES far *NewPrivileges,
	WORD  NewAccessFlags);
```
**Description :**

This function updates an entry in an access control list.  

Unless the user's name is specified to be modified, the information that is not 
specified to be modified remains intact.  If the user's name is specified to be 
modified, the user entry is deleted and a new entry is created.  Unless the 
other access control information is specified to be modified as well, the other 
access control information will be cleared and the user will have No Access to 
the database.

**Parameters :**
Input :
hACL  -  Handle to an access control list.

Name  -  Null-terminated string pointer to user or group to be updated.  Use NULL to update the default name.  If you need to specify a hierarchical user name, be sure to use the fully distinguished name.

UpdateFlags  -   Update flags, ACL_UPDATE_xxx, specifying which fields to update.  These flags may be OR'd together to update multiple fields.

NewName  -  Null-terminated string pointer to new user or group name.  Ignored if UpdateFlags does not indicate that the name is to be updated.  Otherwise, the user entry is deleted and a new entry is created.  Unless the other access control information is specified to be modified as well, the other access control information will be cleared and the user will have No Access to the database.

NewAccessLevel  -  New access level, ACL_LEVEL_xxx.  Ignored if UpdateFlags does not indicate that the access level is to be updated.

NewPrivileges  -  Pointer to new privileges bit mask.  See Data Type, ACL_PRIVILEGES.  Ignored  if UpdateFlags does not indicate that the privileges are to be updated. 

NewAccessFlags  -   New access level modifier flags, ACL_FLAG_xxx  (eg:  unable to delete documents, unable to create documents).  Ignored if UpdateFlags does not indicate that the access level modifier flags are to be updated.

Output :
(routine)  -  Return status from this call - indicates either success (NOERROR), or what the error is.



**See Also :**
[ACL_UPDATE_xxx](/domino-c-api-docs/reference/Symb/ACL_UPDATE_xxx)
[ACL_PRIVILEGES](/domino-c-api-docs/reference/Data/ACL_PRIVILEGES)
[ACL_LEVEL_xxx](/domino-c-api-docs/reference/Symb/ACL_LEVEL_xxx)
[ACL_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACL_FLAG_xxx)
---
