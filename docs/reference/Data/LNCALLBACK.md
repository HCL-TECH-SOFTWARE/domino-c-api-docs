##### Data Type : Standard
##### LNCALLBACK - Calling convention for callback functions.
---
```
#include <global.h>
```

**Definition :**

#if !defined(OS2)

   #define LNCALLBACK FAR PASCAL

#else

   /* OS/2 requires a separate macro because the ordering of function
      modifiers for function pointers is different.  This prevents us
      from inserting _System in a uniform place (e.g. a replacement
      for PASCAL). */

   #define LNCALLBACK _System

#endif

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
[LNCALLBACKPTR](/domino-c-api-docs/reference/Data/LNCALLBACKPTR)
[LNPUBLIC](/domino-c-api-docs/reference/Symb/LNPUBLIC)
[NOTESCALLBACK](/domino-c-api-docs/reference/Data/NOTESCALLBACK)
---
