##### Data Type : Navigators
##### VMODSbigobj - Common fields in Navigator CD records - "Word" signature.
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

The Header field contains a WORD length subfield.  Some Navigator CD records 
use VMODSdrobj, which contains a BYTE length subfield.

**See Also :**
[VMODSrect](/domino-c-api-docs/reference/Data/VMODSrect)
[VIEWMAP_TEXT_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_TEXT_RECORD)
[VMODSdrobj](/domino-c-api-docs/reference/Data/VMODSdrobj)
[VIEWMAP_POLYGON_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_POLYGON_RECORD)
[VIEWMAP_POLYLINE_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_POLYLINE_RECORD)
---
