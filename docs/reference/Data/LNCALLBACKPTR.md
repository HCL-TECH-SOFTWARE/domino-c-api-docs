##### Data Type : Standard
##### LNCALLBACKPTR - Pointer to a callback routine.
---
```
#include <global.h>
```

**Definition :**

#if !defined(OS2)

   #define LNCALLBACKPTR LNCALLBACK FAR *

#else

   /* OS/2 requires a separate macro because the ordering of function
      modifiers for function pointers is different.  This prevents us
      from inserting _System in a uniform place (e.g. a replacement
      for PASCAL). */

   #define LNCALLBACKPTR * _System

#endif

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
[LNCALLBACK](/domino-c-api-docs/reference/Data/LNCALLBACK)
[LNCALLBACKPTR](/domino-c-api-docs/reference/Data/LNCALLBACKPTR)
[NOTESCALLBACK](/domino-c-api-docs/reference/Data/NOTESCALLBACK)
[NOTESCALLBACKPTR](/domino-c-api-docs/reference/Data/NOTESCALLBACKPTR)
---
