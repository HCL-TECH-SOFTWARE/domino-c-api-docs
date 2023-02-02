##### Function : ASP
##### NSFGetOrgDir - Get an organization's data directory (Domino ASP environment).
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFGetOrgDir(**

	char *UserName,
	char *retDir);
**Description :**
This function determines the current organization from the UserName which is 
passed in and returns the data directory for that organization.  This function 
is for use on a Domino ASP server only.
**Parameters :**
Input :
UserName  -  Pointer to a user's name in canonical format.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully got the path to the organization's data directory.


retDir  -  Pointer to a buffer in which the path of the data directory for a particular user's organization is returned.  Declared buffer must be at least MAXPATH characters in length.

**See Also :**
[](D:/md_files/.md)
---
