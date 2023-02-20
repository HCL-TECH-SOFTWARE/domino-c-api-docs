##### Data Type : Composite Data
##### CDCOLORTABLE - Bitmap color table
---
```
#include <editods.h>
```
**Description :**

A color table is one of the optional records following a CDBITMAPHEADER 
record.  The color table specifies the mapping between 8-bit bitmap samples and 
24-bit Red/Green/Blue colors.

The color table consists of a record header, which identifies this as a Color 
Table record, followed by up to 256 3-byte color table entries.  The number of 
color entries is specified in the ColorCount field of CDBITMAPHEADER.  Color 
table entries are only required for the range of color values stored in the 
bitmap;  for example, a bitmap that uses 16 color values (0 to 15) would only 
require 16 color table entries (not the 256 that the 8-bit samples allow).

Each color table entry consists of 3 bytes, Red (byte 0), Green (byte 1), and 
Blue (byte 2).  Each byte is a color value in the range 0 to 255.

**See Also :**
[CDBITMAPHEADER](/reference/Data/CDBITMAPHEADER)
---
