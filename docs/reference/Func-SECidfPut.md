##### Function : ID vault
##### SECidfPut - Upload the ID file contents to the vault.
---
##### #include <idvault.h>
STATUS FAR PASCAL **SECidfPut(**

	char *pUserName,
	char *pPassword,
	char *pIDFilePath,
	KFHANDLE *phKFC,
	char *pServerName,
	DWORD  dwReservedFlags,
	WORD  wReservedType,
	void *pReserved);
**Description :**
Will either open the ID file name provided or use the contents of phKFC if 
provided, locate a vault server for user pUserName, upload the ID file contents 
to the vault, then return with the vault server name in pServerName.
Warning: Please opening a database on the server first through NSFDbOpen()  
before using this function. Consider the sample.
**Parameters :**
Input :
pUserName  -  Name of user whose ID is being put into vault - should be full Notes DN name.

pPassword  -  Password to id file being uploaded to the vault

pIDFilePath  -  Path to id file being uploaded to the vault,may be NULL if phKFC is not NULL

phKFC  -  Pointer to hKFC of ID file being upload to the vault,may be NULL if pIDFilePath is not NULL

pServerName  -  Name of server to contact - on successful return, name of server which has the vault
						should point to a MAXUSERNAME length

dwReservedFlags  -  Reserved flag should be set to 0

wReservedType  -  Reserved type should be set to 0

pReserved  -  Reserved pointer should be set to NULL

Output :
(routine)  -  An ERR status on failure indicating the problem. 


pServerName  -  Name of server to contact - on successful return, name of server which has the vault
						should point to a MAXUSERNAME length

**Sample Usage :**
```
	// Put ID file using local file name and hKFC - only hKFC should be used
	error = SECidfPut (UserName, 
	     "2sherlock2",
	     "c:\\s2.id", 
	     &hKFC, 
	     ServerName, 
	     0, 
	     0,
	     NULL);
```
**See Also :**
[SECidfGet](D:/md_files/SECidfGet.md)
---
