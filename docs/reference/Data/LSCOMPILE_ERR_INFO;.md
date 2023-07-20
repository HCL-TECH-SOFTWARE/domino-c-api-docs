##### Data Type : LotusScript
##### LSCOMPILE_ERR_INFO; - Holds error information when LotusScript code within the note is compiled.
---
```
#include <nsfnote.h>
```

**Definition :**
```
typedef struct
{
	WORD  Version;  /* allows for future expansion - currently always 1 */
	WORD  Line;   /* source line number of error, relative to LotusScript
	        module containing the error, if applicable */
	const char* pErrText;  /* error text */
	const char*     pErrFile;  /* file name, if applicable */
} LSCOMPILE_ERR_INFO;
```

**Description :**

Structure holds information about the error, including specific error text, and also a line number and file name, if applicable.


**See Also :**
[LSCOMPILEERRPROC](/domino-c-api-docs/reference/Data/LSCOMPILEERRPROC)
[NSFNoteLSCompileExt](/domino-c-api-docs/reference/Func/NSFNoteLSCompileExt)
---
