##### Data Type : Composite Data
##### CDIMAGESEGMENT - Structure which defines an image, such as a GIF or JPEG, segment.
---
```
#include <editods.h>
```
**Description :**

This structure defines the image segment data of a JPEG or GIF image and 
follows a CDIMAGEHEADER structure.  The number of segments in the image is 
contained in the CDIMAGEHEADER and specifies the number of CDIMAGESEGMENT 
structures to follow.  An image segment size is 10250 bytes.

The fields in this structure are:

Header  Identifies this as a CDIMAGESEGMENT record.
DataSize  Actual size of image bits in bytes  (10250 per segment).
SeqSize  10250 bytes or less.

**See Also :**
---
