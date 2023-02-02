##### Symbolic Value : Error Handling
##### ERR_xxx - Domino and Notes error codes.
---
##### #include <xxxerr.h>
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
[ERR](D:/md_files/ERR.md)
[errortext](D:/md_files/errortext.md)
[OSLoadString](D:/md_files/OSLoadString.md)
[PKG_xxx](D:/md_files/PKG_xxx.md)
[STATUS](D:/md_files/STATUS.md)
---
