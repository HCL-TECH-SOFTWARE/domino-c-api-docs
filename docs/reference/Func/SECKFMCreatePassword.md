##### Function : User Registration
##### SECKFMCreatePassword - Returns the encoded password, given a non-encoded password.
---
```
#include <kfm.h>
VOID LNPUBLIC SECKFMCreatePassword(

	char far *pPassword,
	KFM_PASSWORD far *retHashedPassword);
```
**Description :**

This function returns the encoded password, given a non-encoded password.

**Parameters :**
Input :
pPassword  -  Non-encoded password.

Output :
(routine)  -  None


retHashedPassword  -  Pointer to the returned encoded password.  This is used in SECKFMGetCertifierCtx to obtain a certifier context.


**See Also :**
[NSFDB2DeleteUsernamePW](/reference/Func/NSFDB2DeleteUsernamePW)
[NSFDB2GetUsernamePW](/reference/Func/NSFDB2GetUsernamePW)
[NSFDB2PutUsernamePW](/reference/Func/NSFDB2PutUsernamePW)
[SECKFMGetCertifierCtx](/reference/Func/SECKFMGetCertifierCtx)
---
