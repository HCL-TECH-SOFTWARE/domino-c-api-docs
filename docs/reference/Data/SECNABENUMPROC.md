##### Data Type : Address Book
##### SECNABENUMPROC - Callback action routine for SECNABEnumerateCertificates.
---
```
#include <nsfsearc.h>
```
**Description :**

This is the datatype of the action routine passed to 
SECNABEnumerateCertificates.

	pCallCtx Pointer to the user defined caller context.
 pCert  Pointer to the certificate being enumerated.
 CertSize Size of the certificate being enumerated.
 Reserved1 Reserved for future use.
 Reserved2 Reserved for future use.



**See Also :**
[SECNABEnumerateCertificates](/domino-c-api-docs/reference/Func/SECNABEnumerateCertificates)
---
