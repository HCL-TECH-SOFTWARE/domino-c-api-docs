##### Symbolic Value : Rich Text
##### CDBITMAP_FLAG_xxx - CDBITMAPHEADER - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	CDBITMAP_FLAG_REQUIRES_PALETTE	  -  Bitmap uses >16 colors or >4 grey scale levels.

	CDBITMAP_FLAG_COMPUTE_PALETTE	  -  Initialized by import code for "first time" importing of bitmaps from clipboard or file, to tell Notes that it should compute whether or not to use a color palette. All imports and API programs should initially set this bit to let the Editor compute whether it needs the palette or not.


**Description :**

Option flags set in the CDBITMAPHEADER record.


**See Also :**
[CDBITMAPHEADER](/domino-c-api-docs/reference/Data/CDBITMAPHEADER)
---
