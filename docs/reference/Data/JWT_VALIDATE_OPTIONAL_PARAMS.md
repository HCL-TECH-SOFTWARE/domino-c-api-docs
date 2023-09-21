##### Data Type : Security
##### JWT_VALIDATE_OPTIONAL_PARAMS - Validates a signed JWT access token.
---
```
#include <bsafe.h>
```

**Definition :**
```
typedef struct {
char *pszCustomClaimName;
ResourceCallback AllowedResource;
ClientCallback AllowedClientID;
void *vpCallerContext; /* caller context data to be passed back to caller */ 
} JWT_VALIDATE_OPTIONAL_PARAMS;

```

**Description :**

Validates a signed JWT access token.<br>
<font color="#121212" face="Arial">#define fJWT_validate_AllowExpired 0x00000001<br>
#define fJWT_validate_AllowMSWorkarounds 0x00000002<br>
#define fJWT_validate_UseCustomEmailClaim 0x00000010<br>
#define fJWT_validate_AllowAlternateAud 0x00000020<br>
#define fJWT_validate_EnforceAllowedClients 0x00000040</font><font size="4"> </font>


**See Also :**
[ArchiveDocumentExport](/domino-c-api-docs/reference/Func/ArchiveDocumentExport)
[ArchiveExportDatabase](/domino-c-api-docs/reference/Func/ArchiveExportDatabase)
---
