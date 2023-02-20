##### Function : Address Book
##### SECNABRemoveCertificate - Remove certificate from an open note.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECNABRemoveCertificate(

	NOTEHANDLE  hNote,
	void *pCertificate,
	DWORD  CertificateSize,
	DWORD  ReservedFlags,
	void *pReserved);
```
**Description :**

Remove certificate from an open note.

**Parameters :**
Input :
hNote  -  Handle to the open note to remove the certificate from.

pCertificate  -  Pointer to the certificate to be removed from the list of certificates in the field name of the open note.

CertificateSize  -  Size of certificate to be removed.

ReservedFlags  -  Reserved, should be set to zero.

pReserved  -  Reserved, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Certificate successfully removed.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 



**See Also :**
[SECNABAddCertificate](/reference/Func/SECNABAddCertificate)
[SECNABEnumerateCertificates](/reference/Func/SECNABEnumerateCertificates)
---
