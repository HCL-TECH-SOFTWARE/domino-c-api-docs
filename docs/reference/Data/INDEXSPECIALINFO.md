##### Data Type : Formula
##### INDEXSPECIALINFO - Index information structure.
---
```
#include <nsfdata.h>
```

**Definition :**

typedef struct {
   DWORD IndexSiblings;    /* # siblings of entry */
   DWORD IndexChildren;    /* # direct children of entry */
   DWORD IndexDescendants; /* # descendants of entry */
   WORD  IndexAnyUnread;   /* TRUE if entry "unread", or any
                              descendants "unread" */
 } INDEXSPECIALINFO;

**Description :**

Index information structure passed into NSFTranslateSpecial() to provide index-related information for certain @INDEX functions, if specified.


**See Also :**
[NSFTranslateSpecial](/domino-c-api-docs/reference/Func/NSFTranslateSpecial)
---
