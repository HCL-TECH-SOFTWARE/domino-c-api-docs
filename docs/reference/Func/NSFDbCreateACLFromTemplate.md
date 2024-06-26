##### Function : Database
##### NSFDbCreateACLFromTemplate - Create access control list from template.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCreateACLFromTemplate(

	DBHANDLE  hNTF,
	DBHANDLE  hNSF,
	const char far *Manager,
	WORD  DefaultAccess,
	DHANDLE far *rethACL);
```
**Description :**

Create a new database access control list using the specified template file.  
The ACL is created in memory so that the ACL can be customized.  The ACL must 
be written to the database using NSFDbStoreACL().  Call OSMemFree() to free the 
memory associated with the rethACL parameter when done with it.

By default, the "owning" server is added to the access control list.  The name 
of the server is obtained from the database handle passed as the argument 
hNSF.  If the owning server is not to be added to the ACL, the value NULLHANDLE 
may be passed for hNSF.

**Parameters :**
Input :
hNTF  -  Handle of the template database.

hNSF  -  Optional;  if not NULLHANDLE, the handle of the Domino database used to supply the owning server name.

Manager  -  Null-terminated string containing the name of the manager for the database.   The manager must be either in canonical fully-qualified form (ie:  CN=John Doe/OU=Documentation/O=WorkSavers) or as a common name (ie:  John Doe).  Do not use abbreviated format.

DefaultAccess  -  If the source template has a [-Default-] entry, then this entry is copied to the -Default- entry in the newly created ACL and this parameter is ignored.  If the source template does not have a [-Default-] entry, then this parameter specifies a WORD value containing the ACL_LEVEL_xxx you wish to assign as the new ACL's -Default- access control level.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - success

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rethACL  -  The handle for the newly-created ACL is stored at this address.


**See Also :**
[NSFDbStoreACL](/domino-c-api-docs/reference/Func/NSFDbStoreACL)
---
