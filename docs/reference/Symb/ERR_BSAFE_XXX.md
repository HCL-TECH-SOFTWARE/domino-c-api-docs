##### Symbolic Value : Security
##### ERR_BSAFE_XXX - SECValidateAccessToken  Flags.
---
```
#include <bsafe.h>
```

**Symbolic Values :**

	ERR_BSAFE_NULLPARAM	  -  Invalid NULL inputs or no trusted OIDC providers.

	ERR_BSAFE_NON_EXISTENT	  -  OIDC Provider not initialized or cannot be used for bearerAuth .

	ERR_BSAFE_TOOSMALL	  -  Email address larger than dwMaxEmailSize.

	ERR_BSAFE_BAD_ATTRIBUTES	  -  JWT lacking mandatory attributes or issuer/aud/scope/azp not matching.

	ERR_BSAFE_CERT_VALIDITY	  -  JWT issued in the future.

	ERR_SECURE_EXPIRED_CERT	  -  JWT expired in the past .

	ERR_BSAFE_BAD_SIGNATURE	  -  Invalid signature on JWT.

	ERR_BSAFE_BAD_OPCODE	  -  Unsupported combination of signing algorithm and key


**Description :**




**See Also :**
---
