##### Symbolic Value : Rich Text
##### LAYOUT_FIELD_FLAG_xxx - CDLAYOUTFIELD flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	LAYOUT_FIELD_FLAG_SINGLELINE	  -  Draw the border with a single line.

	LAYOUT_FIELD_FLAG_VSCROLL	  -  Allow vertical scrolling in the field.

	LAYOUT_FIELD_FLAG_MULTISEL	  -  Allow multiple selections within the field if the field is a listbox or checkbox.

	LAYOUT_FIELD_FLAG_STATIC	  -  Field content is static (cannot be edited).

	LAYOUT_FIELD_FLAG_NOBORDER	  -  Do not draw a border.

	LAYOUT_FIELD_FLAG_IMAGE	  -  Field is displayed as an image, not as text.

The following flags must be the same as LAYOUT_TEXT_FLAG_xxx equivalents:

	LAYOUT_FIELD_FLAG_LTR	  -  Text Left to Right

	LAYOUT_FIELD_FLAG_RTL	  -  Text Right to Left

	LAYOUT_FIELD_FLAG_TRANS	  -  Display with a transparent background.

	LAYOUT_FIELD_FLAG_LEFT	  -  Left-justify text.

	LAYOUT_FIELD_FLAG_CENTER	  -  Center text.

	LAYOUT_FIELD_FLAG_RIGHT	  -  Right-justify text.

	LAYOUT_FIELD_FLAG_VCENTER	  -  Center field contents vertically.


**Description :**

These flags are set in the &quot;Flags&quot; field of a CDLAYOUTFIELD record, and control options for operation of the field in the layout region.


**See Also :**
[CDLAYOUTFIELD](/domino-c-api-docs/reference/Data/CDLAYOUTFIELD)
---
