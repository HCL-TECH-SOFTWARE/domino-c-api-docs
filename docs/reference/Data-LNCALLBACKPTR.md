##### Data Type : Standard
##### LNCALLBACKPTR - Pointer to a callback routine.
---
##### #include <global.h>
**Description :**
Pointer to a callback routine.
**Sample Usage :**
```
Callback pointer declaration from nsfsearc.h:

typedef STATUS (LNCALLBACKPTR NSFSEARCHPROC) (
   void          far * EnumRoutineParameter,
   SEARCH_MATCH  far * SearchMatch,
   ITEM_TABLE    far * SummaryBuffer);
```
**See Also :**
[LNCALLBACK](D:/md_files/LNCALLBACK.md)
[LNCALLBACKPTR](D:/md_files/LNCALLBACKPTR.md)
[NOTESCALLBACK](D:/md_files/NOTESCALLBACK.md)
[NOTESCALLBACKPTR](D:/md_files/NOTESCALLBACKPTR.md)
---
