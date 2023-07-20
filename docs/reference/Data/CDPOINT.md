##### Data Type : Composite Data
##### CDPOINT - Coordinates defining a polygon within an AREA element.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   LONG x;
   LONG y;
} CDPOINT;
```

**Description :**

This structure defines a polygon within a CDAREAELEMENT if the AREA_SHAPE_xxx is an AREA_SHAPE_POLYGON.


**See Also :**
[CDAREAELEMENT](/domino-c-api-docs/reference/Data/CDAREAELEMENT)
---
