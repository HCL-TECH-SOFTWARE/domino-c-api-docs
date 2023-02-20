##### Function : Database
##### NSFDbReadACL - Read in the access control list of a database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbReadACL(

	DBHANDLE  hDB,
	DHANDLE far *rethACL);
```
**Description :**

This function reads the access control list of a database into memory and 
returns a handle to the in-memory copy.  All subsequent access to the access 
control list is carried out via this handle.  If you modify this in-memory copy 
of the access control list, use NSFDbStoreACL to store it in the database.

**Parameters :**
Input :
hDB  -  Handle to the database.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - success

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


rethACL  -  Pointer to the returned handle to the access control list.  Use OSMemFree to free the memory associated with this handle when this handle is not longer needed for processing.


**See Also :**
[ACLCreate](/reference/Func/ACLCreate)
[NSFDbStoreACL](/reference/Func/NSFDbStoreACL)
---
