##### Symbolic Value : Error Handling
##### ERR_xxx - Domino and Notes error codes.
---
```
#include <xxxerr.h>
```
**Description :**

Example (from nsferr.h):

#define     ERR_NOT_NSF   PKG_NSF+1
  errortext(ERR_NOT_NSF, "File is not a database")

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
