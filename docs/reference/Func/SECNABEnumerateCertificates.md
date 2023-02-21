##### Function : Address Book
##### SECNABEnumerateCertificates - Enumerate certificates found in an open note.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECNABEnumerateCertificates(

	NOTEHANDLE  hNote,
	SECNABENUMPROC  CallBack,
	void *pCallCtx,
	DWORD  ReservedFlags,
	void *pReserved);
```
**Description :**

For the open note specified, this function looks for certificates in the field 
name and calls a callback function for each certificate found.

**Parameters :**
Input :
hNote  -  Handle to the open note to be enumerated.

CallBack  -  Callback function to be executed for each certificate found in the field name.   If the return from this user callback is TRUE, then SECNABEnumerateCertificates stops calling this routine.

pCallCtx  -  Caller's context to be passed into the CallBack function.  This user defined context can be used to store the certificate information gathered in the CallBack function.

ReservedFlags  -  Reserved, must be zero.

pReserved  -  Reserved.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - action successful



**See Also :**
[SECNABAddCertificate](/domino-c-api-docs/reference/Func/SECNABAddCertificate)
[SECNABENUMPROC](/domino-c-api-docs/reference/Data/SECNABENUMPROC)
[SECNABRemoveCertificate](/domino-c-api-docs/reference/Func/SECNABRemoveCertificate)
---
