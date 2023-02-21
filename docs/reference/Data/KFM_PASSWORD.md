##### Data Type : User Registration
##### KFM_PASSWORD - Encoded password structure.
---
```
#include <kfm.h>
```
**Description :**

Structure returned by SECKFMCreatePassword to encode a password securely in 
memory to avoid scavenging.  This encoded structure is passed to 
SECKFMGetCertifierCtx to obtain a certifier context.

**See Also :**
[SECKFMCreatePassword](/domino-c-api-docs/reference/Func/SECKFMCreatePassword)
[SECKFMGetCertifierCtx](/domino-c-api-docs/reference/Func/SECKFMGetCertifierCtx)
---
