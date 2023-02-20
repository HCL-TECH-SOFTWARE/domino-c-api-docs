##### Data Type : Mail
##### SECGETSIGNERINFOPROC - Callback action routine for SECGetSignerInfoFromMail.
---
```
#include <kfm.h>
```
**Description :**

This is the datatype of the action routine passed to SECGetSignerInfoFromMail.
      pCallCtx             - (I) callers context passed intothe caller's 
callback routine.
 pCert            - (I) pointer to an asn1encoded certificate
 CertSize             - (I) size of certificate pointed to by pCert
 Reserved1            - (I) reserved, should be ignored
 Reserved2            - (I) reserved, should be ignored

**See Also :**
[SECGetSignerInfoFromMail](/reference/Func/SECGetSignerInfoFromMail)
---
