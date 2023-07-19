##### Data Type : Composite Data
##### CDREGIONBEGIN - Specifies the beginning of a region.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG Header;           /* Signature and length of this record */
   WORD Version;  
   WORD Flags;   
   WORD RegionNum;
   char RegionName[MAXREGIONNAME+1];
} CDREGIONBEGIN;

**Description :**

Header		Signature and Length of this record
<ul><br>
Version		Currently set to 1<br>
Flags		Currently set to zero<br>
RegionNum<br>
RegionName<br>
<br>
This CD Record is used within mail templates.</ul>



**See Also :**
---
