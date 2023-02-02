##### Data Type : Composite Data
##### CDFRAMESET - Used to specify an HTML FRAMESET element
---
##### #include <fsods.h>
**Description :**
Header
Flags   see fFSxxx
BorderEnable  HTML FRAMEBORDER attribute
byAvail1   reserved, must be 0
Reserved1   reserved, must be 0
FrameBorderWidth  HTML BORDER attribute
Reserved3   reserved, must be 0
FrameSpacingWidth HTML FRAMESPACING attribute
Reserved4   reserved, must be 0
ReservedColor1  reserved for future use
ReservedColor2  reserved for future use
RowQty   The number of FRAMESETLENGTH structures defining row information.
ColQty   The number of FRAMESETLENGTH structures defining column information.
Reserved5   reserved, must be 0
Reserved6   reserved, must be 0
FrameBorderColor  HTML BORDERCOLOR attribute, see COLOR_VALUE
Reserved7[2]  reserved, must be 0

A FRAMESETLENGTH structure will follow depending on the value found in either 
RowQty or ColQty.  There could be multiple FRAMESETLENGTH structures defining 
the RowQty and ColQty values.
**See Also :**
[CDFRAME](D:/md_files/CDFRAME.md)
[CDFRAMESETHEADER](D:/md_files/CDFRAMESETHEADER.md)
[COLOR_VALUE](D:/md_files/COLOR_VALUE.md)
[fFSxxx](D:/md_files/fFSxxx.md)
[FRAMESETLENGTH](D:/md_files/FRAMESETLENGTH.md)
---
