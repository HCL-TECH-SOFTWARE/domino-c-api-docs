##### Data Type : Mail
##### SECGETSIGNERINFOPROC - Callback action routine for SECGetSignerInfoFromMail.
---
```
#include <kfm.h>
```

**Definition :**

typedef BOOL (LNCALLBACKPTR SECGETSIGNERINFOPROC) (void  *pCallCtx,
	         void  *pCert,
	         DWORD CertSize,
	             WORD  Reserved1,
	         WORD  Reserved2);

**Description :**

This is the datatype of the action routine passed to<tt><font size="2">&nbsp;SECGetSignerInfoFromMail.</font></tt>
<ul><br>
      pCallCtx             - (I) callers context passed intothe caller's callback routine.<br>
	pCert 	          - (I) pointer to an asn1encoded certificate<br>
	CertSize             - (I) size of certificate pointed to by pCert<br>
	Reserved1            - (I) reserved, should be ignored<br>
	Reserved2            - (I) reserved, should be ignored</ul>



**See Also :**
[SECGetSignerInfoFromMail](/domino-c-api-docs/reference/Func/SECGetSignerInfoFromMail)
---
