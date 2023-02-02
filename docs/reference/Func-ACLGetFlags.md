##### Function : Access Control List
##### ACLGetFlags - Return flags that apply to the entire ACL.
---
##### #include <acl.h>
STATUS LNPUBLIC **ACLGetFlags(**

	DHANDLE  hACL,
	DWORD far *Flags);
**Description :**
Return the DWORD of flags that apply to this whole access control list.
**Parameters :**
Input :
hACL  -  Handle of the access control list.

Output :
(routine)  -  NOERROR - Successfully retrieved flags
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



Flags  -  ACL-wide flags.

**See Also :**
[ACLSetFlags](D:/md_files/ACLSetFlags.md)
[ACL_xxx](D:/md_files/ACL_xxx.md)
---
