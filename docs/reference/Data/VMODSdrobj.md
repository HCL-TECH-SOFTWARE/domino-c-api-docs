##### Data Type : Navigators
##### VMODSdrobj - Common fields in Navigator CD records - "Byte" signature.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   BSIG      Header;
   VMODSrect ObjRect;
   WORD      flags;
   WORD      NameLen;
   WORD      LabelLen;
   FONTID    FontID;
   WORD      TextColor;
   WORD      Alignment;
   WORD      bWrap;
   DWORD     spare[4]; /* for future use */
} VMODSdrobj;
```

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
The Header field contains a BYTE length subfield.  Some Navigator CD records use VMODSbigobj, which contains a WORD length subfield.</ul>



**See Also :**
[VMODSbigobj](/domino-c-api-docs/reference/Data/VMODSbigobj)
[VMODSrect](/domino-c-api-docs/reference/Data/VMODSrect)
[VIEWMAP_RECT_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_RECT_RECORD)
[VIEWMAP_BITMAP_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_BITMAP_RECORD)
[VIEWMAP_REGION_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_REGION_RECORD)
---
