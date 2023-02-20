##### Function : User Registration
##### SECKFMGetCertifierCtx - Get certifier context
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMGetCertifierCtx(

	char far *pCertFile,
	KFM_PASSWORD far *pKfmPW,
	char far *pLogFile,
	TIMEDATE far *pExpDate,
	char far *retCertName,
	HCERTIFIER far *rethKfmCertCtx,
	BOOL far *retfIsHierarchical,
	WORD far *retwFileVersion);
```
**Description :**

This function gets the handle to a certifier context of the given certifier id 
file.  When done with the certifier context, you are responsible for freeing 
this memory by calling SECKFMFreeCertifierCtx().

**Parameters :**
Input :
pCertFile  -  Pathname of the certifier id file.

pKfmPW  -  Optional.  Pointer to KFM_PASSWORD structure, which contains the  certifier's encoded password.  Use SECKFMCreatePassword to fill in this structure with the encoded password, given a non-encoded password.  If NULL is passed in, and a certifier password is required, you will be prompted to enter the password.

pLogFile  -  Pathname of the certifier's log file.  This parameter is required for Domino installations that use the Administration Process so that when using other C API function that require a Certifier Context, the proper entries will be entered in the Certification Log file (CERTLOG.NSF) .  If your Domino installation does not include a Certification Log (does not use the Administration Process), then you should pass in NULL for this parameter.

pExpDate  -  Pointer to the certificate expiration date for the entity that is being certified.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - action successful

ERR_xxx  -  Various OS, and KFM errors.


retCertName  -  Returned name of certifier.

rethKfmCertCtx  -  Pointer to returned handle of certifier context.

retfIsHierarchical  -  Contains TRUE if certifier is hierarchical, otherwise FALSE.

retwFileVersion  -  Pointer to the returned version of the certifier.


**See Also :**
[REGNewCertifier](/reference/Func/REGNewCertifier)
[REGNewWorkstation](/reference/Func/REGNewWorkstation)
[SECKFMCreatePassword](/reference/Func/SECKFMCreatePassword)
---
