##### Data Type : Navigators
##### VMODSbigobj - Common fields in Navigator CD records - "Word" signature.
---
```
#include <vmods.h>
```

**Definition :**

typedef struct {
   WSIG      Header;
   VMODSrect ObjRect;
   WORD      flags;
   WORD      NameLen;
   WORD      LabelLen;
   FONTID    FontID;
   WORD      TextColor;
   WORD      Alignment;
   WORD      bWrap;
   DWORD     spare[4]; /* for future use */
} VMODSbigobj;

**Description :**

This structure contains fields common to the composite data records for the graphical objects in a Navigator.  The fields in this structure are:
<ul><br>

<ul>Header		Signature identifying the type of Navigator CD record.<br>
ObjRect	Bounding rectangle for this graphical object.   See VMODSrect.<br>
flags		Option flags.   Set to 7.<br>
NameLen	Length of the name for the graphical object;  may be 0.<br>
LabelLen	Length of the displayed label of the graphical object;  may be 0.<br>
FontID		Font ID to use when displaying the label.   See FONTID.<br>
TextColor	Color to use for the label text.   Use NOTES_COLOR_xxx value.<br>
Alignment	Alignment of the label text.   Set to 0.<br>
bWrap		If TRUE, apply word-wrap when displaying the label.<br>
spare		Reserved;  must be 0.</ul>
<br>
The Header field contains a WORD length subfield.  Some Navigator CD records use VMODSdrobj, which contains a BYTE length subfield.</ul>



**See Also :**
[VMODSrect](/domino-c-api-docs/reference/Data/VMODSrect)
[VIEWMAP_TEXT_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_TEXT_RECORD)
[VMODSdrobj](/domino-c-api-docs/reference/Data/VMODSdrobj)
[VIEWMAP_POLYGON_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_POLYGON_RECORD)
[VIEWMAP_POLYLINE_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_POLYLINE_RECORD)
---
