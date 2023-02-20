##### Data Type : Standard
##### LNCALLBACKPTR - Pointer to a callback routine.
---
```
#include <global.h>
```
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
[LNCALLBACK](/reference/Data/LNCALLBACK)
[LNCALLBACKPTR](/reference/Data/LNCALLBACKPTR)
[NOTESCALLBACK](/reference/Data/NOTESCALLBACK)
[NOTESCALLBACKPTR](/reference/Data/NOTESCALLBACKPTR)
---
