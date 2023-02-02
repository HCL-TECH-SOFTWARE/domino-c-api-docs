##### Data Type : Composite Data
##### CDIMAGEHEADER - Structure which defines an image,such as a GIF or JPEG, header.
---
##### #include <editods.h>
**Description :**
This structure is used to define a JPEG or GIF Image that is part of a Domino 
document.  The CDIMAGEHEADER structure follows a CDGRAPHIC structure.  
CDIMAGESEGMENT structure(s) then follow the CDIMAGEHEADER.

The fields in this structure are:

Header  Identifies this as a CDIMAGEHEADER record (SIG_CD_IMAGEHEADER).
ImageType  Type of Image (see CDIMAGETYPE_xxx)
Width    Width of image.
Height  Height of image.
ImageDataSize the file length of the image.
SegCount  the number of segments in this image (filelength of image / 10250 
(segment size)).
Flags  Image flag values (currently unused).
Reserved  unused.
**See Also :**
[CDGRAPHIC](D:/md_files/CDGRAPHIC.md)
[CDIMAGESEGMENT](D:/md_files/CDIMAGESEGMENT.md)
[CDIMAGETYPE_xxx](D:/md_files/CDIMAGETYPE_xxx.md)
---
