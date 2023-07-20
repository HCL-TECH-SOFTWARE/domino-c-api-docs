##### Data Type : Composite Data
##### CDREGIONEND - Specifies the ending of a region.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;           /* Signature and length of this record */
   WORD RegionNum;
   char RegionName[MAXREGIONNAME+1];
} CDREGIONEND;
```

**Description :**

Header		Signature and length of this record
<ul><br>
RegionNum<br>
RegionName</ul>



**See Also :**
---
