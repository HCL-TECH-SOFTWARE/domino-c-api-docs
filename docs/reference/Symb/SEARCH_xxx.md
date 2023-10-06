##### Symbolic Value : Miscellaneous
##### SEARCH_xxx - NSFSearch() - SearchFlags
---
```
#include <nsfsearc.h>
```

**Symbolic Values :**

	SEARCH_ALL_VERSIONS	  -  Include deleted and non-matching notes in the search. (This is always ON for time-delimited searches.)

	SEARCH_SUMMARY	  -  Return summary buffer with each match. If this flag is not set, the ITEM_TABLE far *SummaryBuffer input parameter to the action routine is NULL.

	SEARCH_FILETYPE	  -  Search a directory instead of a database.

	SEARCH_NOTIFYDELETIONS	  -  Set NOTE_CLASS_NOTIFYDELETION bit of NOTE_CLASS for deleted notes.

	SEARCH_ALLPRIVS	  -  Return an error if we don't have full privileges for this search.

	SEARCH_SESSION_USERNAME	  -  Use current session's user name, not server's.

	SEARCH_NOABSTRACTS	  -  Filter out "Truncated" documents.

	SEARCH_DATAONLY_FORMULA	  -  Search formula applies only to data notes, i.e., others match.
	
	SEARCH2_LARGE_BUCKETS   -  return flag in orig structs if > MAXONESEGSIZE.


**Description :**

Use these flags in the search_flags parameter to NSFSearch to control what the function searches for and what information it returns. These values can be bitwise-ORed together to combine functionality.


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
[NSFSearch](/domino-c-api-docs/reference/Func/NSFSearch)
---
