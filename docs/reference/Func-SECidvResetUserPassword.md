##### Function : Security
##### SECidvResetUserPassword - Set a password associated with a user's ID file stored in the ID vault. 
---
##### #include <idvault.h>
STATUS LNPUBLICFUNC **SECidvResetUserPassword(**

	char *pServer,
	char *pUserName,
	char *pPassword,
	WORD  wDownloadCount,
	DWORD  ReservedFlags,
	void *pReserved);
**Description :**
This password is required by the user when they recover their ID file from the 
ID vault.
**Parameters :**
Input :
pServer  -  Name of server to contact to request the password reset. Can be NULL if executed from a program or agent on a server. Does NOT have to be a vault server. But must be running Domino 8.5 or later. 

pUserName  -  Name of user to reset their vault id file password.

pPassword  -  New password to set in the vault record for pUserName.

wDownloadCount  -  If this user's effective policy setting document has "allow automatic ID downloads" set to no, then this parameter specifies how many downloads the user an now perform. If downloads are automatic this setting should be zero.

ReservedFlags  -  Must be set to zero.

pReserved  -  Must be set to NULL.


**See Also :**
[](D:/md_files/.md)
---
