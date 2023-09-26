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
#define fJWT_validate_AllowExpired 0x00000001 // Treat expired JWTs as valid. Should only be used for testing purposes<br>
#define fJWT_validate_AllowMSWorkarounds 0x00000002 // Equivalent to setting the &quot;Allow Microsoft Workarounds&quot; checkbox in idpcat. See the feature documentation for details.<br>
#define fJWT_validate_UseCustomEmailClaim 0x00000010 // Indicates that vpOptionalParams points to a JWT_VALIDATE_OPTIONAL_PARAMS structure with a non-NULL pszCustomClaimName holding the name of the JWT Claim to be used instead of &quot;email&quot; when finding the user's name.<br>
#define fJWT_validate_AllowAlternateAud 0x00000020 // Indicates that vpOptionalParams points to a JWT_VALIDATE_OPTIONAL_PARAMS structure with a valid AllowedResource callback function pointer. This callback will be invoked for each aud Claim in the JWT and should return TRUE if the value matches an allowed resource for this site.<br>
#define fJWT_validate_EnforceAllowedClients 0x00000040 // Indicates that vpOptionalParams points to a JWT_VALIDATE_OPTIONAL_PARAMS structure with a valid AllowedClientID callback function pointer. This callback will be invoked with the azp Claim if any in the JWT and should return TRUE if this azp Claim value matches the client_id for an OAuth client that is allowed to access this site.


**See Also :**
[SECTOKENFREE](./SECTOKENFREE)
[SECTOKENGENERATE](./SECTOKENGENERATE)
---
