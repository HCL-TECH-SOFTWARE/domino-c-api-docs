##### Function : User Registration
##### SECKFMSetCertifierExpiration - Set the certificate expiration date.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMSetCertifierExpiration(

	HCERTIFIER  hKfmCertCtx,
	TIMEDATE far *pExpirationDate);
```
**Description :**

This function sets the certificate expiration date for the entity that is being 
certified.

**Parameters :**
Input :
hKfmCertCtx  -  Handle of a certifier context obtained from calling SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).

pExpirationDate  -  Pointer to the the certificate expiration date for the entity that is being certified.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - action successful

ERR_xxx  -  Various OS, and KFM errors.



**See Also :**
[REGNewCertifier](/domino-c-api-docs/reference/Func/REGNewCertifier)
[REGNewWorkstation](/domino-c-api-docs/reference/Func/REGNewWorkstation)
[SECKFMGetCertifierCtx](/domino-c-api-docs/reference/Func/SECKFMGetCertifierCtx)
---
