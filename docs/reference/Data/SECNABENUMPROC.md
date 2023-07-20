##### Data Type : Address Book
##### SECNABENUMPROC - Callback action routine for SECNABEnumerateCertificates.
---
```
#include <nsfsearc.h>
```

**Definition :**
```
typedef BOOL (LNCALLBACKPTR SECNABENUMPROC)(
      void  *pCallCtx,
      void  *pCert,
      DWORD CertSize,
      WORD  Reserved1,
      WORD  Reserved2);
```

**Description :**

This is the datatype of the action routine passed to SECNABEnumerateCertificates.<br>
<br>
	pCallCtx	Pointer to the user defined caller context.<br>
	pCert		Pointer to the certificate being enumerated.<br>
	CertSize	Size of the certificate being enumerated.<br>
	Reserved1	Reserved for future use.<br>
	Reserved2	Reserved for future use.<br>



**See Also :**
[SECNABEnumerateCertificates](/domino-c-api-docs/reference/Func/SECNABEnumerateCertificates)
---
