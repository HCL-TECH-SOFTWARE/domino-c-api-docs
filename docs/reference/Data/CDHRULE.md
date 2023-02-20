##### Data Type : Rich Text
##### CDHRULE - Horizontal line.
---
```
#include <editods.h>
```
**Description :**

Specifies a horizontal line.  The fields in this structure are:

Header  Defines this composite data item as a CDHRULE item.
Flags  Optional flags;  see HRULE_FLAG_xxx for flag values.
Width  Specifies the horizontal length of the line in TWIPS (see the symbolic 
definition for ONEINCH for more information).  Use DEFAULTHRULEWIDTH for the 
default.
Height  Specifies the height of the line (or thickness) in TWIPS.  Use 
DEFAULTHRULEHEIGHT for the default.
Color  Specifies the color used to draw the line (see the symbolic values for 
NOTES_COLOR_xxx for more information).
GradientColor Specifies the gradient color used to draw the line (see the 
symbolic values for NOTES_COLOR_xxx for more information).


**See Also :**
[CDHORIZONTALRULE_VERSIONxxx](/reference/Symb/CDHORIZONTALRULE_VERSIONxxx)
[DEFAULTHRULExxx](/reference/Symb/DEFAULTHRULExxx)
[HRULE_FLAG_xxx](/reference/Symb/HRULE_FLAG_xxx)
[NOTES_COLOR_xxx](/reference/Symb/NOTES_COLOR_xxx)
[ONEINCH](/reference/Symb/ONEINCH)
---
