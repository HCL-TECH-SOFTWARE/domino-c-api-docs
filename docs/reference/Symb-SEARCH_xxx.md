##### Symbolic Value : Miscellaneous
##### SEARCH_xxx - NSFSearch() - SearchFlags
---
##### #include <nsfsearc.h>
**Description :**
Use these flags in the search_flags parameter to NSFSearch to control what the 
function searches for and what information it returns. These values can be 
bitwise-ORed together to combine functionality.
**Sample Usage :**
```

    if (error = NSFSearch (
        db_handle,          /* database handle */
        NULLHANDLE,         /* selection formula */
        NULL,               /* title of view in selection formula */
        SEARCH_SUMMARY,     /* search flags: get summary data! */
        NOTE_CLASS_DOCUMENT,    /* note class to find */
        NULL,               /* starting date (unused) */
        ReadSummaryData,    /* action routine for notes found */
        NULL,               /* argument to action routine */
        NULL))              /* returned ending date (unused) */

    {
        printf ("Error: unable to search database.\n");
        NSFDbClose (db_handle);
        return (ERR(error));
    }
```
**See Also :**
[NSFSearch](D:/md_files/NSFSearch.md)
---
