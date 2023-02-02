##### Function : Address Book
##### SECNABAddCertificate - Add certificate to an open note.
---
##### #include <kfm.h>
STATUS LNPUBLIC **SECNABAddCertificate(**

	NOTEHANDLE  hNote,
	void *pCertificate,
	DWORD  CertificateSize,
	DWORD  ReservedFlags,
	void *pReserved);
**Description :**
Add certificate to an open note.
**Parameters :**
Input :
hNote  -  Handle to the open note that the certificate is to be inserted into.

pCertificate  -  Pointer to DER encoded certificate (not HAC, no leading notes version or size fields) to be appended to the list.

CertificateSize  -  Length of DER.

ReservedFlags  -  Reserved, should be set to zero.

pReserved  -  Reserved, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Certificate successfully added.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


**See Also :**
[SECNABEnumerateCertificates](D:/md_files/SECNABEnumerateCertificates.md)
[SECNABRemoveCertificate](D:/md_files/SECNABRemoveCertificate.md)
---
