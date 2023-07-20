##### Data Type : Rich Text
##### CDHRULE - Horizontal line.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header; /* Signature and length of this record. */
   DWORD Flags; 
   WORD  Width;
   WORD  Height;
   WORD  Color;
   WORD  GradientColor;
} CDHRULE;
```

**Description :**

Specifies a horizontal line.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDHRULE item.<br>
Flags		Optional flags;  see HRULE_FLAG_xxx for flag values.<br>
Width		Specifies the horizontal length of the line in TWIPS (see the symbolic definition for ONEINCH for more information).  Use DEFAULTHRULEWIDTH for the default.<br>
Height		Specifies the height of the line (or thickness) in TWIPS.  Use DEFAULTHRULEHEIGHT for the default.<br>
Color		Specifies the color used to draw the line (see the symbolic values for NOTES_COLOR_xxx for more information).<br>
GradientColor	Specifies the gradient color used to draw the line (see the symbolic values for NOTES_COLOR_xxx for more information).</ul>
</ul>



**See Also :**
[CDHORIZONTALRULE_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDHORIZONTALRULE_VERSIONxxx)
[DEFAULTHRULExxx](/domino-c-api-docs/reference/Symb/DEFAULTHRULExxx)
[HRULE_FLAG_xxx](/domino-c-api-docs/reference/Symb/HRULE_FLAG_xxx)
[NOTES_COLOR_xxx](/domino-c-api-docs/reference/Symb/NOTES_COLOR_xxx)
[ONEINCH](/domino-c-api-docs/reference/Symb/ONEINCH)
---
