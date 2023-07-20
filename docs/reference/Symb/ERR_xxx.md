##### Symbolic Value : Error Handling
##### ERR_xxx - Domino and Notes error codes.
---
```
#include <xxxerr.h>
```

**Symbolic Values :**

	ERR_xxx	  -  see Description


**Description :**

Example (from nsferr.h):
<ul><br>
<br>
<tt><font size="2">#define &nbsp; &nbsp; ERR_NOT_NSF &nbsp; PKG_NSF+1<br>
 &nbsp;errortext(ERR_NOT_NSF, &quot;File is not a database&quot;)</font></tt></ul>



**Sample Usage :**
```
STATUS      error;
char        szNotesError[MAX_NOTES_ERROR];

if (error = NSFDbOpen(szName))
{
    OSLoadString(NULLHANDLE, ERR(error), szNotesError,
                 MAX_NOTES_ERROR);
    printf("Unable to open database: %s.\n", szNotesError);
    return;
}
```

**See Also :**
[ERR](/domino-c-api-docs/reference/Func/ERR)
[errortext](/domino-c-api-docs/reference/Symb/errortext)
[OSLoadString](/domino-c-api-docs/reference/Func/OSLoadString)
[PKG_xxx](/domino-c-api-docs/reference/Symb/PKG_xxx)
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
---
