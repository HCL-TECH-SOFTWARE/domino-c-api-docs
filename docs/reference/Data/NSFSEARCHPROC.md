##### Data Type : Search
##### NSFSEARCHPROC - Callback action routine for NSFSearch
---
```
#include <nsfsearc.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR NSFSEARCHPROC)(
   void far *         EnumRoutineParameter,
   SEARCH_MATCH far * SearchMatch,
   ITEM_TABLE far *   SummaryBuffer);
```

**Description :**

This is the datatype of the action routine passed to NSFSearch.


**See Also :**
[NSFSearch](/domino-c-api-docs/reference/Func/NSFSearch)
---
