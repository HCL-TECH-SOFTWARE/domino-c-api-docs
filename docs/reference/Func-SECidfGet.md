##### Function : ID vault
##### SECidfGet - Get the id file from the vault
---
##### #include <idvault.h>
STATUS FAR PASCAL **SECidfGet(**

	char *pUserName,
	char *pPassword,
	char *pPutIDFileHere,
	KFHANDLE *phKFC,
	char *pServerName,
	DWORD  dwReservedFlags,
	WORD  wReservedType,
	void *pReserved);
**Description :**
Will contact the server and locate a vault for pUserName. Then extract the ID 
file from the vault and write it to pPutIDFileHere, and/or open down loaded ID 
file into an hKFC, if successful returns with the vault server name in 
pServerName.

**Parameters :**
Input :
pUserName  -  Name of user whose ID is being put into vault - should be full Notes DN name.	

pPassword  -  Password to id file being uploaded to the vault

pServerName  -  Name of server to contact - on successful return, name of server which has the vault,should point to a MAXUSERNAME length

dwReservedFlags  -  Reserved flag should be set to 0

wReservedType  -  Rserved type should be set to 0
	

Output :
(routine)  -  An ERR status on failure indicating the problem. 


pPutIDFileHere  -  Path to where the download ID file should be created or overwritten,may be NULL if phKFC is not NULL

phKFC  -  Pointer receive the hKFC of the ID file down loaded file from the vault,may be NULL if pPutIDFileHere is not NULL

pServerName  -  Name of server to contact - on successful return, name of server which has the vault,should point to a MAXUSERNAME length

**Sample Usage :**
```
	// Get id file to local file name and hKFC
	error = SECidfGet (UserName, 
	  "2sherlock2",
	  "c:\\s2.id", 
	  &hKFC2, 
	  ServerName, 
	  0,
	  0,
	  NULL);
```
**See Also :**
[SECidfPut](D:/md_files/SECidfPut.md)
---
