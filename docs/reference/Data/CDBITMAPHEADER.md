##### Data Type : Composite Data
##### CDBITMAPHEADER - Header record for a Bitmap
---
```
#include <editods.h>
 CDBITMAPHEADER(
void);
```
**Description :**

A rich text field may contain a bitmap image.  There are three types, 
monochrome, 8-bit mapped color, and 16-bit color;  a gray scale bitmap is 
stored as an 8-bit color bitmap with a color table having entries [0, 0, 0], 
[1, 1, 1], . . . , [255, 255, 255].  All bitmaps are stored as a single plane 
(some graphics devices support multiple planes).

Color tables must be provided for 8-bit color bitmaps (which includes gray 
scale bitmaps);  no color table is needed for monochrome or 16-bit color 
bitmaps.  In 16-color bitmaps, 1 word of 16 bits is stored for each pixel.  The 
high-order bit of this word will be 0.  The rest of the word is divided into 3 
fields of 5 bits each to store the Red, Green, and Blue color values, allowing 
32 levels per color.

Release 2.0 of Notes used version 1 of the Notes graphics drivers.  In Release 
3.0 of Notes, version 2 of the graphics drivers allowed omission of the color 
table for 8-bit color bitmaps that only used the 16 standard Windows colors.  
In this case, the "Flags" word of the CDBITMAPHEADER will have the bit 
CDBITMAP_FLAG_REQUIRES_PALETTE set to 0.

In order to be displayed, a CDGRAPHIC record must precede a CDBITMAPHEADER 
record.  A bitmap begins with a CDBITMAPHEADER record which defines the size 
and display characteristics.

        Header                      Tag identifying this as a CDBITMAPHEADER 
record
        Dest                            Destination bitmap height and width in 
pixels
        Crop                            Reserved
        Flags                           If CDBITMAP_FLAG_REQUIRES_PALETTE is 
set, the color table is required
        wReserved               Reserved
        lReserved                 Reserved
        Width                           Width of bitmap in pixels
        Height                          Height of bitmap in pixels
        BitsPerPixel               Bits per pixel - must be 1, 8, or 16
        SamplesPerPixel    For 1 or 8 bits per pixel, this is set to 1;  for 16 
bits per pixel, 3
        BitsPerSample         For 1 bit per pixel, this is set to 1;  for 8 
bits, 8;  for 16 bits, 5
        SegmentCount         Number of CDBITMAPSEGMENT records
        ColorCount                Number of entries in the CDCOLORTABLE record 
(0-256)
        PatternCount             Number of entries in the CDPATTERNTABLE (0-64)

The CDBITMAPHEADER may be followed immediately by an optional 
CDTRANSPARENTTABLE record, which is subsequently followed by an optional 
CDCOLORTABLE record, an optional CDPATTERNTABLE record, and one or more 
CDBITMAPSEGMENT records containing the compressed bitmap data.  Details of the 
basic compression scheme are provided in the description of the CDBITMAPSEGMENT 
record.

Bitmap data may also be compressed by using a pattern table.  See the 
description of CDPATTERNTABLE for details.  A bitmap using a pattern table 
cannot be created using the C API;  the PatternCount field must be set to 0.


**Parameters :**



**See Also :**
[CDBITMAPSEGMENT](/domino-c-api-docs/reference/Data/CDBITMAPSEGMENT)
[CDBITMAP_FLAG_xxx](/domino-c-api-docs/reference/Symb/CDBITMAP_FLAG_xxx)
[CDCOLORTABLE](/domino-c-api-docs/reference/Data/CDCOLORTABLE)
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CDPATTERNTABLE](/domino-c-api-docs/reference/Data/CDPATTERNTABLE)
[CDTRANSPARENTTABLE](/domino-c-api-docs/reference/Data/CDTRANSPARENTTABLE)
---
