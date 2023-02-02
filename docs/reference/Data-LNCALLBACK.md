##### Data Type : Standard
##### LNCALLBACK - Calling convention for callback functions.
---
##### #include <global.h>
**Description :**
Calling convention for callback functions.
**Sample Usage :**
```
/* C API include files */

#include <global.h>
#include <nsfdb.h>
#include <nsfnote.h>
#include <nsfsearc.h>
#include <osmem.h>
#include <nsferr.h>


/* Global data */

STATUS result;

/* Callback function declaration */

STATUS LNCALLBACK print_fields (
    void         far * db_handle,
    SEARCH_MATCH far * search_info,
    ITEM_TABLE   far * summary_info)
{
    . . .
}

    . . .

/* Passing address of the callback to Domino or Notes */

   result = NSFSearch (
      db_handle,      /* database handle */
      formula_handle, /* selection formula */
      NULL,           /* title of view in selection formula */
      0,              /* search flags */
      NOTE_CLASS_DOCUMENT,/* note class to find */
      NULL,           /* starting date (unused) */
      print_fields,   /* call function for each note found */
      &db_handle,     /* argument to print_fields */
      NULL);          /* returned ending date (unused) */
```
**See Also :**
[LNCALLBACKPTR](D:/md_files/LNCALLBACKPTR.md)
[LNPUBLIC](D:/md_files/LNPUBLIC.md)
[NOTESCALLBACK](D:/md_files/NOTESCALLBACK.md)
---
