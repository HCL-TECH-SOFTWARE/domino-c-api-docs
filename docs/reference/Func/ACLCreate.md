##### Function : Access Control List
##### ACLCreate - Creates an access control list.
---
```
#include <acl.h>
STATUS LNPUBLIC ACLCreate(

	DHANDLE far *rethACL);
```
**Description :**

This function creates an access control list for a database and should only be 
used when the API program creates a new database with NSFDbCreate.  Otherwise, 
NSFDbReadACL should be used to read in an existing access control list.  
Databases created through Domino Designer or Notes will contain an access 
control list.  

The returned handle is a handle to an in-memory copy of an ACL.  All subsequent 
access to it is carried out via this handle.  Use NSFDbStoreACL to store the 
in-memory copy of the ACL in the database.  Use OSMemFree to deallocate the 
list.

**Parameters :**

Output :
(routine)  -  Return status from this call - indicates either success (NOERROR), or what the error is.


rethACL  -  Pointer to returned handle to an access control list.  Use OSMemFree to free the memory associated with this handle when this handle is not longer needed for processing.


**See Also :**
[NSFDbReadACL](./reference/Func/NSFDbReadACL)
[NSFDbStoreACL](./reference/Func/NSFDbStoreACL)
---
