##### Data Type : User Registration
##### KFM_PASSWORD - Encoded password structure.
---
```
#include <kfm.h>
```

**Definition :**
```
typedef struct {
   BYTE Type;               /* Type of hash.  This value should be  */
      /* interpreted only by the lower Notes   */
      /* layers and never by software above the */
      /* API layer. */
   BYTE HashedPassword[48]; /* Hashed password */
} KFM_PASSWORD;
```

**Description :**

Structure returned by SECKFMCreatePassword to encode a password securely in memory to avoid scavenging.  This encoded structure is passed to SECKFMGetCertifierCtx to obtain a certifier context.


**See Also :**
[SECKFMCreatePassword](/domino-c-api-docs/reference/Func/SECKFMCreatePassword)
[SECKFMGetCertifierCtx](/domino-c-api-docs/reference/Func/SECKFMGetCertifierCtx)
---
