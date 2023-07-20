##### Symbolic Value : Rich Text
##### LAYOUT_TEXT_FLAG_xxx - CDLAYOUTTEXT flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	LAYOUT_TEXT_FLAG_TRANS	  -  Display with a transparent background.

	LAYOUT_TEXT_FLAG_LEFT	  -  Left-justify text.

	LAYOUT_TEXT_FLAG_CENTER	  -  Center text.

	LAYOUT_TEXT_FLAG_RIGHT	  -  Right-justify text.

	LAYOUT_TEXT_FLAG_ALIGN_MASK	  -  Mask used to obtain only the text alignment bits.

	LAYOUT_TEXT_FLAG_VCENTER	  -  Center field contents vertically.

	LAYOUT_TEXT_FLAG_LTR	  -  Left to right order text.

	LAYOUT_TEXT_FLAG_RTL	  -  Right to left order text.

	LAYOUT_TEXT_FLAG_RO_MASK	  -  Read only mask.

	LAYOUT_TEXT_FLAGS_MASK	  -  Mask used to obtain only the valid text layout flag bits.


**Description :**

These flags are set in the &quot;Flags&quot; field of a CDLAYOUTTEXT record, and control operation of the field in the layout region.


**See Also :**
[CDLAYOUTTEXT](/domino-c-api-docs/reference/Data/CDLAYOUTTEXT)
---
