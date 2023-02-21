##### Data Type : Navigators
##### VIEWMAP_BITMAP_RECORD - Navigator bitmap graphic CD record.
---
```
#include <vmods.h>
```
**Description :**

The VIEWMAP_BITMAP_RECORD stores a bitmap in a Navigator.  This record is 
stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the 
Navigator.  The fields in this structure are:

DRObj  Common fields, including VIEWMAP_BITMAP_RECORD signature.
DataLen Number of bytes occupied by bitmap data.
xBytes  Width of bitmap, in bytes.
yBits  Height of bitmap, in bits.
zBits  "Depth" of bitmap (number of color planes), in bits.
spare  Reserved;  must be 0.

This structure is followed by the bitmap name and the display label (if any) in 
packed format (no terminating NUL), then by the bitmap data.


**See Also :**
[VMODSdrobj](/domino-c-api-docs/reference/Data/VMODSdrobj)
---
