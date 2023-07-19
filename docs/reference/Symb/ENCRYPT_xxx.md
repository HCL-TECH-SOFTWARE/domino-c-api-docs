##### Symbolic Value : Note
##### ENCRYPT_xxx - NSFNoteCopyAndEncrypt() - EncryptFlags
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	ENCRYPT_WITH_USER_PUBLIC_KEY	  -  Encrypt the message with the key in the user's ID. This flag is not for outgoing mail messages because recipients, other than the sender, will not be able to decrypt the message. This flag can be useful to encrypt documents in a local database to keep them secure or to encrypt documents that can only be decrypted by the same user.

	ENCRYPT_SMIME_IF_MIME_PRESENT	  -  Encrypt SMIME if MIME present.

	ENCRYPT_SMIME_NO_SENDER	  -  Encrypt SMIME no sender.

	ENCRYPT_SMIME_TRUST_ALL_CERTS	  -  Encrypt SMIME trusting all certificates.


**Description :**

Optional flag for NSFNoteCopyAndEncrypt.


**See Also :**
[NSFNoteCopyAndEncrypt](/domino-c-api-docs/reference/Func/NSFNoteCopyAndEncrypt)
---
