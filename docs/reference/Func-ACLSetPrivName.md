##### Function : Access Control List
##### ACLSetPrivName - Given a privilege number, set the given privilege name.
---
##### #include <acl.h>
STATUS LNPUBLIC **ACLSetPrivName(**

	DHANDLE  hACL,
	WORD  PrivNum,
	char far *PrivName);
**Description :**
This function associates a privilege name (role) with a given privilege number 
(0 through ACL_PRIVCOUNT - 1).   Privilege names associated with privilege 
numbers 0 through 4 are privilege levels compatible with versions of Notes 
prior to Release 3.  When displayed by Notes or returned by ACLGetPrivName, 
they are enclosed in parenthesis.  Privilege names associated with privilege 
numbers 5 through ACL_PRIVCOUNT - 1 are members of the access role list.  When 
displayed by Notes or returned by ACLGetPrivName, they are enclosed in 
brackets.
**Parameters :**
Input :
hACL  -   Handle to an access control list.

PrivNum  -  Privilege number (0 through ACL_PRIVCOUNT - 1).

PrivName  -   Pointer to the null-terminated privilege or role name string to be associated with the given number.  Limited to ACL_PRIVNAMEMAX characters, including the null terminator.

Output :
(routine)  -   Return status from this call - indicates either success (NOERROR), or what the error is.


**See Also :**
[ACLGetPrivName](D:/md_files/ACLGetPrivName.md)
---
