##### Data Type : Navigators
##### VIEWMAP_BITMAP_RECORD - Navigator bitmap graphic CD record.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   VMODSdrobj DRobj;
   WORD       DataLen;
   WORD       xBytes;   /* width in bytes */
   WORD       yBits;    /* height in bits */
   WORD       zBits;    /* depth in bits */
   DWORD      spare[4]; /* for future use */
} VIEWMAP_BITMAP_RECORD;
```

**Description :**

The VIEWMAP_BITMAP_RECORD stores a bitmap in a Navigator.  This record is stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the Navigator.  The fields in this structure are:
<ul><br>

<ul>DRObj		Common fields, including VIEWMAP_BITMAP_RECORD signature.<br>
DataLen	Number of bytes occupied by bitmap data.<br>
xBytes		Width of bitmap, in bytes.<br>
yBits		Height of bitmap, in bits.<br>
zBits		&quot;Depth&quot; of bitmap (number of color planes), in bits.<br>
spare		Reserved;  must be 0.</ul>
<br>
This structure is followed by the bitmap name and the display label (if any) in packed format (no terminating NUL), then by the bitmap data.</ul>



**See Also :**
[VMODSdrobj](/domino-c-api-docs/reference/Data/VMODSdrobj)
---
