##### Data Type : Composite Data
##### CDIMAGESEGMENT - Structure which defines an image, such as a GIF or JPEG, segment.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   LSIG Header;   /* Signature and Length */
   WORD DataSize; /* Actual Size of image bits in bytes, ignoring
                     any filler */
   WORD SegSize;  /* Size of segment, is equal to or larger than
                     DataSize if filler byte added to maintain word
                     boundary */
} CDIMAGESEGMENT;

**Description :**

This structure defines the image segment data of a JPEG or GIF image and follows a CDIMAGEHEADER structure.  The number of segments in the image is contained in the CDIMAGEHEADER and specifies the number of CDIMAGESEGMENT structures to follow.  An image segment size is 10250 bytes.
<ul><br>
<br>
The fields in this structure are:<br>
<br>
Header		Identifies this as a CDIMAGESEGMENT record.<br>
DataSize		Actual size of image bits in bytes  (10250 per segment).<br>
SeqSize		10250 bytes or less.</ul>



**See Also :**
---
