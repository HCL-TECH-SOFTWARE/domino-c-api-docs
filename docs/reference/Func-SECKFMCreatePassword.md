##### Function : User Registration
##### SECKFMCreatePassword - Returns the encoded password, given a non-encoded password.
---
##### #include <kfm.h>
VOID LNPUBLIC **SECKFMCreatePassword(**

	char far *pPassword,
	KFM_PASSWORD far *retHashedPassword);
**Description :**
This function returns the encoded password, given a non-encoded password.
**Parameters :**
Input :
pPassword  -  Non-encoded password.

Output :
(routine)  -  None


retHashedPassword  -  Pointer to the returned encoded password.  This is used in SECKFMGetCertifierCtx to obtain a certifier context.

**See Also :**
[NSFDB2DeleteUsernamePW](D:/md_files/NSFDB2DeleteUsernamePW.md)
[NSFDB2GetUsernamePW](D:/md_files/NSFDB2GetUsernamePW.md)
[NSFDB2PutUsernamePW](D:/md_files/NSFDB2PutUsernamePW.md)
[SECKFMGetCertifierCtx](D:/md_files/SECKFMGetCertifierCtx.md)
---
