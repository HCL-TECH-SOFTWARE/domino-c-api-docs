##### Symbolic Value : Character Manipulation
##### NLS_xxx (TRANSLATE) - Control flags used by the function NLS_translate.
---
```
#include <nls.h>
```

**Symbolic Values :**

	NLS_NONULLTERMINATE	  -  Does not add a NULL to the end of the translated result.

	NLS_NULLTERMINATE	  -  Adds a NULL to the end of the translated result.

	NLS_STRIPUNKNOWN	  -  Strips unknown characters.

	NLS_TARGETISLMBCS	  -  Converts target string to LMBCS.

	NLS_SOURCEISLMBCS	  -  Converts source string from LMBCS.

	NLS_TARGETISUNICODE	  -  Converts target string to UNICODE.

	NLS_SOURCEISUNICODE	  -  Converts source string from UNICODE.

	NLS_TARGETISPLATFORM	  -  Converts target string to the encoding used by the host OS.

	NLS_SOURCEISPLATFORM	  -  Converts source string from the encoding used by the host OS.


**Description :**

Control flags used by the function NLS_translate to govern how the translation is performed.


**See Also :**
[ACLGetHistory](/domino-c-api-docs/reference/Func/ACLGetHistory)
[NLS_translate](/domino-c-api-docs/reference/Func/NLS_translate)
---
