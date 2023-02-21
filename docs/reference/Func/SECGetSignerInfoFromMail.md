##### Function : Mail
##### SECGetSignerInfoFromMail - Enumerate the certificates out of a SMIME signature
---
```
#include <kfm.h>
STATUS LNPUBLIC SECGetSignerInfoFromMail(

	DHANDLE  hNote,
	SECGETSIGNERINFOPROC  Callback,
	void *pCallCtx,
	DWORD  ReservedFlags,
	void *pReserved);
```
**Description :**

Will enumerate the certificates out of a SMIME signature and call a user 
callback routine for each internet certificate found.

**Parameters :**
Input :
hNote  -  note handle to find the signers internet certificates if the note was SMIME signed

Callback  -  a callback function to be called for every internet certificate found in the SMIME signature.

pCallCtx  -  a context that the user can have passed into the callback routine.

ReservedFlags  -  should be set to 0. Reserved.

pReserved  -  should be set to NULL. Reserved.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - action successful



**See Also :**
[SECGETSIGNERINFOPROC](/domino-c-api-docs/reference/Data/SECGETSIGNERINFOPROC)
[SECNABEnumerateCertificates](/domino-c-api-docs/reference/Func/SECNABEnumerateCertificates)
---
