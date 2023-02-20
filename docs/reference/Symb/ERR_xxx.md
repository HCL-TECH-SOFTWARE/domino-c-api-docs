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
[ERR](/reference/Func/ERR)
[errortext](/reference/Symb/errortext)
[OSLoadString](/reference/Func/OSLoadString)
[PKG_xxx](/reference/Symb/PKG_xxx)
[STATUS](/reference/Data/STATUS)
---
