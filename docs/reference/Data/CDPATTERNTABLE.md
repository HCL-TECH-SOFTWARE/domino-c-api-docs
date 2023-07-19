##### Data Type : Composite Data
##### CDPATTERNTABLE - Bitmap pattern table
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
 LSIG Header;
 /* One or more pattern table entries */
} CDPATTERNTABLE;

**Description :**

A pattern table is one of the optional records following a CDBITMAPHEADER record.  The pattern table is used to compress repetitive bitmap data.<br>
<br>
The pattern table consists of a record header, which identifies this as a Pattern Table record, followed by up to 64 pattern table entries.  The number of pattern table entries is specified in the PatternCount field of the CDBITMAPHEADER record.<br>
<br>
Each pattern table entry consists of a fixed number of bytes;  the number of bytes in each entry that is actually used will depend on the color representation used for the bitmap.  There is space in each entry for up to three bytes for each picture element.  Since the constant PELS_PER_PATTERN is currently defined to be 8, this means that each entry in the pattern table will occupy 24 bytes.<br>
<br>
If the bitmap uses the 8-bit mapped color representation, the bitmap contains less than 256 different colors.  Each picture element is represented as a single byte containing an index into the color table.  In this case, only the first 8 bytes of each 24-byte pattern table entry will be occupied, and the remaining 16 bytes are ignored.<br>
<br>
If the bitmap uses an RGB color representation, each picture element is represented by 3 bytes, Red (byte 0), Green (byte 1), and Blue (byte 2).  Each byte is a color value in the range 0 to 255.  (This is the same color entry format used in a CDCOLORTABLE).  In this case, all 24 bytes of each pattern table entry will be used.


**See Also :**
[CDBITMAPHEADER](/domino-c-api-docs/reference/Data/CDBITMAPHEADER)
[CDCOLORTABLE](/domino-c-api-docs/reference/Data/CDCOLORTABLE)
---
