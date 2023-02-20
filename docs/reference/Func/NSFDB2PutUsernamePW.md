##### Function : Database
##### NSFDB2PutUsernamePW - Store a DB2 username and password in a Notes ID file.
---
```
#include <kfm.h>

STATUS LNPUBLIC NSFDB2PutUsernamePW(

	char *ServerName,
	char *pFilename,
	char *UserName,
	char *Password,
	KFM_PASSWORD *pKfmPW);
```
**Description :**

This function will store a DB2 username and password in a specified Notes ID 
file.

**Parameters :**
Input :
ServerName  -  Pointer to a null-terminated character string containing the name of the server on which the ID resides.  NULL for local.

pFilename  -  Pointer to a null-terminated character string containing the name of the user ID to put the user's DB2 username and password.  NULL if current ID is to be used.

UserName  -  Pointer to a null-terminated character string containing the name of the DB2 user to store in the ID.

Password  -  Pointer to a null-terminated character string containing the password of the DB2 user to store in the ID.

pKfmPW  -  Pointer to the encoded password structure containing the user's hashed password.  NULL if current ID is in use or no password.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[KFM_PASSWORD](/reference/Data/KFM_PASSWORD)
[NSFDB2DeleteUsernamePW](/reference/Func/NSFDB2DeleteUsernamePW)
[NSFDB2GetUsernamePW](/reference/Func/NSFDB2GetUsernamePW)
[SECKFMCreatePassword](/reference/Func/SECKFMCreatePassword)
---
