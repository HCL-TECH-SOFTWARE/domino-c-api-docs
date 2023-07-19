##### Data Type : Composite Data
##### CDIMAGEHEADER - Structure which defines an image,such as a GIF or JPEG, header.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   LSIG  Header;        /* Signature and Length */
   WORD  ImageType;     /* Type of image (e.g., GIF, JPEG) */
   WORD  Width;         /* Width of the image (in pixels) */
   WORD  Height;        /* Height of the image (in pixels) */
   DWORD ImageDataSize; /* Size (in bytes) of the image data */
   DWORD SegCount;      /* Number of CDIMAGESEGMENT records
                           expected to follow */
   DWORD Flags;         /* Flags (currently unused) */
   DWORD Reserved;      /* Reserved for future use */
} CDIMAGEHEADER;

**Description :**

This structure is used to define a JPEG or GIF Image that is part of a Domino document.  The CDIMAGEHEADER structure follows a CDGRAPHIC structure.  CDIMAGESEGMENT structure(s) then follow the CDIMAGEHEADER.
<ul><br>
<br>
The fields in this structure are:<br>
<br>
Header		Identifies this as a CDIMAGEHEADER record (SIG_CD_IMAGEHEADER).<br>
ImageType		Type of Image (see CDIMAGETYPE_xxx)<br>
Width  		Width of image.<br>
Height		Height of image.<br>
ImageDataSize	the file length of the image.<br>
SegCount		the number of segments in this image (filelength of image / 10250 (segment size)).<br>
Flags		Image flag values (currently unused).<br>
Reserved		unused.</ul>



**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CDIMAGESEGMENT](/domino-c-api-docs/reference/Data/CDIMAGESEGMENT)
[CDIMAGETYPE_xxx](/domino-c-api-docs/reference/Symb/CDIMAGETYPE_xxx)
---
