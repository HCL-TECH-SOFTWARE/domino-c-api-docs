##### Function : Database
##### NSFDB2DeleteUsernamePW - Remove a user's DB2 username and password.
---
```
#include <kfm.h>

STATUS LNPUBLIC NSFDB2DeleteUsernamePW(

	char *ServerName,
	char *pFilename,
	KFM_PASSWORD *pKfmPW);
```
**Description :**

This function will clear a DB2 username and password stored in a Notes ID file.

**Parameters :**
Input :
ServerName  -  Pointer to a null-terminated character string containing the name of the server on which the ID resides.  NULL for local.

pFilename  -  Pointer to a null-terminated character string containing the name of the user ID to remove the user's DB2 username and password from.  NULL if current ID is to be used.

pKfmPW  -  Pointer to an encoded password structure containing the user's hashed password.    NULL if current ID is in use or no password.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[KFM_PASSWORD](/domino-c-api-docs/reference/Data/KFM_PASSWORD)
[NSFDB2GetUsernamePW](/domino-c-api-docs/reference/Func/NSFDB2GetUsernamePW)
[NSFDB2PutUsernamePW](/domino-c-api-docs/reference/Func/NSFDB2PutUsernamePW)
[SECKFMCreatePassword](/domino-c-api-docs/reference/Func/SECKFMCreatePassword)
---
