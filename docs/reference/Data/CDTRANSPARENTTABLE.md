##### Data Type : Composite Data
##### CDTRANSPARENTTABLE - Bitmap transparency table.
---
```
#include <editods.h>
```
**Description :**

Bitmap Transparency Table (optionally one per bitmap).  The colors in this 
table specify the bitmap colors that are "transparent".  The pixels in the 
bitmap whose colors are in this table will not affect the background; the 
background will "bleed through" into the bitmap.  The entries in the 
transparency table should be in the same format as entries in the color table.  
If a transparency table is used for a bitmap, it must immediately follow the 
CDBITMAPHEADER.

**See Also :**
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
