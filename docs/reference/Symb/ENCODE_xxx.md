##### Symbolic Value : File Attachment
##### ENCODE_xxx - Miscellaneous FILEOBJECT flags.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	ENCODE_MASK	  -  File object has mime content transfer encoding.

	ENCODE_NONE	  -  No encoding.

	ENCODE_BASE64	  -  Base64 encoding.

	ENCODE_QP	  -  Quoted-printable encoding.

	ENCODE_UUENCODE	  -  X-uuencode encoding.

	ENCODE_EXTENSION	  -  Unknown extension encoding.


**Description :**

These values may be used in the Flags member of the FILEOBJECT structure.


**See Also :**
[FILEOBJECT](/domino-c-api-docs/reference/Data/FILEOBJECT)
---
