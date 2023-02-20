##### Function : Access Control List
##### ACLGetAdminServer - Get the administration server for this ACL
---
```
#include <acl.h>
STATUS LNPUBLIC ACLGetAdminServer(

	DHANDLE  hList,
	char far *ServerName);
```
**Description :**

Obtain the name of the server that is identified in the access control list as 
the administration server.

**Parameters :**
Input :
hList  -  Handle of the access control list.

Output :
(routine)  -  NOERROR - Successfully retrieved administrative server name
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



ServerName  -  The null-terminated name of the admin server is placed at this address.  If there is no admin server for this ACL, the string will consist of just the null terminator.


**See Also :**
[ACLSetAdminServer](/reference/Func/ACLSetAdminServer)
---
