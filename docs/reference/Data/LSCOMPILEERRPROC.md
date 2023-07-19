##### Data Type : LotusScript
##### LSCOMPILEERRPROC - Callback action routine for NSFNoteLSCompileExt.
---
```
#include <nsfnote.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR LSCOMPILEERRPROC)(
	const LSCOMPILE_ERR_INFO* pInfo, 
	void* pCtx);

**Description :**

The callback function is only called if there were any compilation errors. <br>

<ul>   pInfo             - (I) pointer to a LSCOMPILE_ERR_INFO structure.<br>
   pCtx             - (I) pointer to the user-defined data.</ul>



**See Also :**
[LSCOMPILE_ERR_INFO;](/domino-c-api-docs/reference/Data/LSCOMPILE_ERR_INFO;)
[NSFNoteLSCompileExt](/domino-c-api-docs/reference/Func/NSFNoteLSCompileExt)
---
