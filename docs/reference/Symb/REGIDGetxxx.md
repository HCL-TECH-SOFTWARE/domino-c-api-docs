##### Symbolic Value : User Registration
##### REGIDGetxxx - Information type codes for ID files.
---
```
#include <reg.h>
```

**Symbolic Values :**

	REGIDGetUSAFlag	  -  Return a Boolean value of size sizeof(BOOL) that is TRUE if the ID is North American.

	REGIDGetHierarchicalFlag	  -  Return a Boolean value of size sizeof(BOOL) that is TRUE if the ID is hierarchical.

	REGIDGetSafeFlag	  -  Return a Boolean value of size sizeof(BOOL) that is TRUE if the ID is a safe copy.

	REGIDGetCertifierFlag	  -  Return a Boolean value of size sizeof(BOOL) that is TRUE if the ID is a certifier.

	REGIDGetNotesExpressFlag	  -  Return a Boolean value of size sizeof(BOOL) that is TRUE if the ID is a Notes Express ID.

	REGIDGetDesktopFlag	  -  Return a Boolean value of size sizeof(BOOL) that is TRUE if the ID is desktop only.

	REGIDGetName	  -  Return the name from the ID file. The name may be 0 to MAXUSERNAME bytes in length.

	REGIDGetPublicKey	  -  Return the public key from the ID file.

	REGIDGetPrivateKey	  -  Return the private key from the ID file.

	REGIDGetIntlPublicKey	  -  Return the international public key from the ID file.

	REGIDGetIntlPrivateKey	  -  Return the international private key from the ID file.


**Description :**

Information type codes used by REGGetIDInfo() to identify the data items to be obtained from an ID file.<br>
<br>
When an ID is made Safe, the Certifier, NotesExpress, and Desktop flags are cleared, so these flags will always be FALSE in a Safe copy.<br>
<br>
Flat IDs do not distinguish between users and certifiers, so the Certifier flag will always be FALSE if the Hierarchical flag is FALSE.


**See Also :**
[REGGetIDInfo](/domino-c-api-docs/reference/Func/REGGetIDInfo)
---
