##### Data Type : Mixed 32/16-bit Model
##### NOTESCALLBACKPTR - * OBSOLETE * Pointers to callback functions
---
##### #include <global.h>
**Description :**
***OBSOLETE - Included for backward compatibility only***

Different compilers supported when using the mixed 32/16-bit model require the 
use of different syntax to declare pointers to callback functions.  This macro 
isolates these syntax differences.  Normally, this macro is only used in the 
Notes API header files, and is not needed in application programs.  However, if 
an application program will be manipulating pointers to callback functions, 
this macro will simplify the pointer declarations.
**Sample Usage :**
```
Callback pointer declaration from nsfsearc.h:

    typedef STATUS (NOTESCALLBACKPTR NSFSEARCHPROC) (
        void          NOTESPTR EnumRoutineParameter,
        SEARCH_MATCH  NOTESPTR SearchMatch,
        ITEM_TABLE    NOTESPTR SummaryBuffer);
```
**See Also :**
[LNCALLBACK](D:/md_files/LNCALLBACK.md)
[LNCALLBACKPTR](D:/md_files/LNCALLBACKPTR.md)
[NOTESCALLBACK](D:/md_files/NOTESCALLBACK.md)
---
