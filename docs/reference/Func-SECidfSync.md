##### Function : ID vault
##### SECidfSync - Synch the ID file contents to the vault
---
##### #include <idvault.h>
STATUS FAR PASCAL **SECidfSync(**

	char *pUserName,
	char *pPassword,
	char *pIDFilePath,
	KFHANDLE *phKFC,
	char *pServerName,
	DWORD  dwReservedFlags,
	WORD  wReservedType,
	void *pReserved,
	DWORD *retdwFlags);
**Description :**
Will either open the ID file name provided or use the contents of phKFC if 
provided, locate a vault server, synch the ID file contents to the vault, then 
return the synched content in *phKFC and/or pIDFilePath.If successful the vault 
server name is retuned in pServerName.

**Parameters :**
Input :
pUserName  -  Name of user whose ID is being synched with the vault copy - should be full Notes DN name

pPassword  -  Password to id file stored in the vault

pIDFilePath  -  Path to id file being synched to the vault,may be NULL if phKFC is not NULL

phKFC  -  Pointer to hKFC of ID file being upload to the vault,may be NULL if pIDFilePath is not NULL	

dwReservedFlags  -  Reserved flag should be set to 0

wReservedType  -  Reserved type should be set to 0

pReserved  -  Reserved pointer should be set to NULL

Output :
(routine)  -  An ERR status on failure indicating the problem. 


pIDFilePath  -  Path to id file being synched to the vault,may be NULL if phKFC is not NULL

phKFC  -  Pointer to hKFC of ID file being upload to the vault,may be NULL if pIDFilePath is not NULL

retdwFlags  -  Set to valus below based on results
retdwFlags values
#define IDV_syncRetFlag_IDSyncDone            1
#define IDV_syncRetFlag_IDFoundInVault        2
#define IDV_syncRetFlag_IDNotFoundInVault    4



**Sample Usage :**
```
// Sync the hKFC with the ID file in the Vault and write to S2.id and hKFC
	error = SECidfSync (UserName, "2sherlock2",
	  "c:\\s2.id", 
	  &hKFC2, 
	  ServerName, 
	  0,
	  0,
	  NULL, 
	  &VaultFlags);
```
**See Also :**
[SECidfGet](D:/md_files/SECidfGet.md)
[SECidfPut](D:/md_files/SECidfPut.md)
---
