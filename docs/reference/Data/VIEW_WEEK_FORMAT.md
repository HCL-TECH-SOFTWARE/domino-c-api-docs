##### Data Type : Views
##### VIEW_WEEK_FORMAT - Header structure used in VIEW_CALENDAR_FORMAT
---
```
#include <viewfmt.h>
```

**Definition :**
```
typedef struct {
   VIEW_FORMAT_HEADER Header;
} VIEW_WEEK_FORMAT;
```

**Description :**

This defines the structure of a header member of the VIEW_CALENDAR_FORMAT structure.  The VIEW_CALENDAR_FORMAT structure is part of a VIEW_CALENDAR_FORMAT_ITEM, which is an item in a calendar view note.  The structure is the same as the VIEW_FORMAT_HEADER structure.


**See Also :**
[VIEW_FORMAT_HEADER](/domino-c-api-docs/reference/Data/VIEW_FORMAT_HEADER)
[VIEW_CALENDAR_FORMAT](/domino-c-api-docs/reference/Data/VIEW_CALENDAR_FORMAT)
---
