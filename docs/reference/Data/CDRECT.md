##### Data Type : Composite Data
##### CDRECT - Coordinates of a rectangle or circle within an AREA element.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   LONG left;
   LONG top;
   LONG right;
   LONG bottom;
} CDRECT;
```

**Description :**

This structure defines either a rectangle or a circle within a CDAREAELEMENT if the AREA_SHAPE_xxx is an AREA_SHAPE_RECT or AREA_SHAPE_CIRCLE.


**See Also :**
[AREA_SHAPE_xxx](/domino-c-api-docs/reference/Symb/AREA_SHAPE_xxx)
[CDAREAELEMENT](/domino-c-api-docs/reference/Data/CDAREAELEMENT)
---
