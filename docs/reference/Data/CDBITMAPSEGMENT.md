##### Data Type : Composite Data
##### CDBITMAPSEGMENT - Bitmap data segment
---
```
#include <editods.h>
```
**Description :**

The bitmap data is divided into segments to optimize data storage within 
Domino.  It is recommended that each segment be no larger than 10k bytes.  For 
best display speed, the segments sould be as large as possible, up to the 
practical 10k limit.  A scanline must be contained within a single segment, and 
cannot be divided between two segments.  A bitmap must contain at least one 
segment, but may have many segments.

Bitmap data is compressed using a simple run-length encoding.  Each raster line 
is encoded separately (i. e., the run length of a compressed segment won't 
exceed the length of a raster line).  Raster lines are not padded beyond a byte 
boundary;  each scanline ends on the byte boundary defined by the width of the 
bitmap.

In the run-length encoding scheme, a flag/length field is followed by the byte 
or bytes to be repeated.  The flag occupies the high-order 2 bits.  The length 
field may be either 6 bits (so the flag/length field occupies one byte) or 14 
bits (so the flag/length field occupies two bytes), indicated by the two-bit 
flag values:

 11 = 6-bit repeat count of compressed pixels
 10 = 14-bit count of compressed pixels to repeat
 01 = 14-bit count of pattern entries to repeat (see CDPATTERNTABLE)
         00 = 6-bit count of raw (uncompressed) pixels

The illustrations shown below under "Sample Code" may make this clearer.

For monochrome or 8-bit color bitmaps, there is one byte of data following the 
flag/length field;  for 16-bit color bitmaps, there are two bytes of data.

**Sample Usage :**
```
Domino proprietary bitmap compression scheme description
-------------------------------------------------------

The basic form used is a run length encoding scheme,
where there is one of four escape codes followed by either 
a run length byte or word which is then followed by the 
byte or pattern to repeat.  Here is the summary of the 
escape codes and their definitions:


 MSB<---------->LSB
 +-----------------------------------+
(1) | 1 1 c c c c c c | r r r r r r r r |
 +-----------------------------------+
  cccccc = six bit repeat count
  rrrrrrrr = PELS to repeat


 MSB<---------------------------->LSB
 +-----------------------------------------------------+
(2) | 1 0 c c c c c c | c c c c c c c c | r r r r r r r r |
	+-----------------------------------------------------+
  cccccccccccccc = 14 bit repeat count
  rrrrrrrr = PELS to repeat


 MSB<---------------------------->LSB
 +-----------------------------------------------------+
(3) | 0 1 c c c c c c | c c c c c c c c | r r r r r r r r |
 +-----------------------------------------------------+
  cccccccccccccc = 14 bit repeat count
  rrrrrrrr = Pattern table index of pattern to repeat 


 MSB<---------->LSB
 +------------------------------------------------------
(4) | 0 0 c c c c c c | r r r r r r r r |[r r r r r r r r]|...
 +------------------------------------------------------
  cccccc = 6 bit repeat count
  r[cccccc] = 1 or more raw uncompressed PELS  


Note that in schemes (1),(2) and (4) the picture elements may be 
one or more bytes in length depending upon the number of bytes
per PEL, which is determined by the bitmap header info. Also
note that scheme (3) uses pattern table indexing. A pattern is
an 8 PEL repeating sequence.  For full-color (>256 colors) 
bitmaps, a color table is NOT used, and a packed 16 bit RGB
representation is used which saves one byte per PEL over 
traditional 24 bit representation, and still yields 32768 
possible colors (5 bits of R,G,B intensity)

```
**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CDBITMAPHEADER](/domino-c-api-docs/reference/Data/CDBITMAPHEADER)
---
