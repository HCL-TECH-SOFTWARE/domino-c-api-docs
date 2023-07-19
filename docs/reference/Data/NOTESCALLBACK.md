##### Data Type : Mixed 32/16-bit Model
##### NOTESCALLBACK - * OBSOLETE * Calling convention for callback functions
---
```
#include <global.h>
```

**Definition :**

#define NOTESCALLBACK LNCALLBACK

**Description :**

***OBSOLETE - Included for backward compatibility only***
<ul><br>
<br>
This macro defines the calling convention used for callback functions - application functions called from within Notes.  In the mixed 32/16-bit model for OS/2 2.1, the application callback functions are 32-bit code.  Notes will attempt to call the function using the 16-bit Pascal calling convention.  To support this, the macro specifies that callback functions use the 16-bit &quot;_Far16 _Pascal&quot; calling convention.  Under Windows and OS/2 1.x, the calling convention used is &quot;FAR PASCAL&quot;.  On other platforms, this macro is null;  no special calling convention is used.</ul>



**Sample Usage :**
```
/* Notes API include files */

#include <global.h>
#include <nsfdb.h>
#include <nsfnote.h>
#include <nsfsearc.h>
#include <osmem.h>
#include <nsferr.h>


/* Global data */

STATUS result;

/* Callback function declaration */

STATUS NOTESCALLBACK print_fields (
    void         NOTESPTR db_handle,
    SEARCH_MATCH NOTESPTR search_info,
    ITEM_TABLE   NOTESPTR summary_info
) {
        . . .
}

        . . .

/* Passing address of the callback to Notes */

    result = NSFSearch (
        db_handle,      /* database handle */
        formula_handle, /* selection formula */
        NULL,           /* title of view in selection formula */
        0,              /* search flags */
        NOTE_CLASS_DATA,/* note class to find */
        NULL,           /* starting date (unused) */
        print_fields,   /* call function for each note found */
        &db_handle,     /* argument to print_fields */
        NULL);          /* returned ending date (unused) */
```

**See Also :**
[LNCALLBACK](/domino-c-api-docs/reference/Data/LNCALLBACK)
[NOTESAPI](/domino-c-api-docs/reference/Data/NOTESAPI)
[NOTESAPICDECL](/domino-c-api-docs/reference/Data/NOTESAPICDECL)
[NOTESCALLBACKPTR](/domino-c-api-docs/reference/Data/NOTESCALLBACKPTR)
[NotesMain](/domino-c-api-docs/reference/Func/NotesMain)
---
