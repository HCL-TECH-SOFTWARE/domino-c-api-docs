##### Function : Access Control List
##### ACLDeleteEntry - Deletes an entry from an access control list.
---
##### #include <acl.h>
STATUS LNPUBLIC **ACLDeleteEntry(**

	DHANDLE  hACL,
	const char far *Name);
**Description :**
This function deletes an entry from an access control list.
**Parameters :**
Input :
hACL  -  Handle to an access control list.

Name  -  Null-terminated string pointer to user or group to be deleted.  If you need to specify a hierarchical user name, be sure to use the fully distinguished name.

Output :
(routine)  -   Return status from this call - indicates either success (NOERROR), or what the error is.


**See Also :**
[ACLCreate](D:/md_files/ACLCreate.md)
[ACLAddEntry](D:/md_files/ACLAddEntry.md)
---
