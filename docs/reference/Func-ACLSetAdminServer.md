##### Function : Access Control List
##### ACLSetAdminServer - Change the ACL administration server
---
##### #include <acl.h>
STATUS LNPUBLIC **ACLSetAdminServer(**

	DHANDLE  hList,
	char far *ServerName);
**Description :**
Change the name of the administration server for the access control list.  The 
server name must be in canonical (fully-qualified) form;  the canonical form of 
the name can be obtained with the function DNCanonicalize().
**Parameters :**
Input :
hList  -  Handle of the Access Control List.

ServerName  -  Name of the new admin server.

Output :
(routine)  -  NOERROR - Successfully retrieved administrative server name
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**See Also :**
[ACLGetAdminServer](D:/md_files/ACLGetAdminServer.md)
[DNCanonicalize](D:/md_files/DNCanonicalize.md)
---
