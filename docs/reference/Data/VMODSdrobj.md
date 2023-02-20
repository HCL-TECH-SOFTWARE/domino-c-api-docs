##### Data Type : Navigators
##### VMODSdrobj - Common fields in Navigator CD records - "Byte" signature.
---
```
#include <vmods.h>
```
**Description :**

This structure contains fields common to the composite data records for the 
graphical objects in a Navigator.  The fields in this structure are:

Header  Signature identifying the type of Navigator CD record.
ObjRect Bounding rectangle for this graphical object.   See VMODSrect.
flags  Option flags.   Set to 7.
NameLen Length of the name for the graphical object;  may be 0.
LabelLen Length of the displayed label of the graphical object;  may be 0.
FontID  Font ID to use when displaying the label.   See FONTID.
TextColor Color to use for the label text.   Use NOTES_COLOR_xxx value.
Alignment Alignment of the label text.   Set to 0.
bWrap  If TRUE, apply word-wrap when displaying the label.
spare  Reserved;  must be 0.

The Header field contains a BYTE length subfield.  Some Navigator CD records 
use VMODSbigobj, which contains a WORD length subfield.

**See Also :**
[VMODSbigobj](/reference/Data/VMODSbigobj)
[VMODSrect](/reference/Data/VMODSrect)
[VIEWMAP_RECT_RECORD](/reference/Data/VIEWMAP_RECT_RECORD)
[VIEWMAP_BITMAP_RECORD](/reference/Data/VIEWMAP_BITMAP_RECORD)
[VIEWMAP_REGION_RECORD](/reference/Data/VIEWMAP_REGION_RECORD)
---
