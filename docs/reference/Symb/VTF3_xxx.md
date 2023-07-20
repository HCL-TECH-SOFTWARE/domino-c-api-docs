##### Symbolic Value : Composite Data
##### VTF3_xxx - VIEW_TABLE_FORMAT3 - Flags
---
```
#include <viewfmt.h>
```

**Symbolic Values :**

	VTF3_S_GridStyleSolid	  -  (Shift) View grid lines use solid line.

	VTF3_M_GridStyleSolid	  -  (Mask) View grid lines use solid line.

	VTF3_S_GridStyleDash	  -  (Shift) View grid lines use dashes.

	VTF3_M_GridStyleDash	  -  (Mask) View grid lines use dashes.

	VTF3_S_GridStyleDot	  -  (Shift) View grid lines use dots.

	VTF3_M_GridStyleDot	  -  (Mask) View grid lines use dots.

	VTF3_S_GridStyleDashDot	  -  (Shift) View grid lines use dashes and dots.

	VTF3_M_GridStyleDashDot	  -  (Mask) View grid lines use dashes and dots.

	VTF3_S_AllowCustomizations	  -  (Shift) View customizations on/off .

	VTF3_M_AllowCustomizations	  -  (Mask) View customizations on/off .

	VTF3_S_EvaluateActionsHideWhen	  -  (Shift) View actions evaluate hide when.

	VTF3_M_EvaluateActionsHideWhen	  -  (Mask) View actions evaluate hide when.

	VTF3_S_HideLeftMarginBorder	  -  (Shift) Hide border after left margin.

	VTF3_M_HideLeftMarginBorder	  -  (Mask) Hide border after left margin.

	VTF3_S_BoldUnreadRows	  -  (Shift) Bold the unread rows.

	VTF3_M_BoldUnreadRows	  -  (Mask) Bold the unread rows.

	VTF3_S_AllowCreateNewDoc	  -  (Shift) Inviewedit-newdocs in view.

	VTF3_M_AllowCreateNewDoc	  -  (Mask) Inviewedit-newdocs in view.

	VTF3_S_HasBackgroundImage	  -  (Shift) View has background image.

	VTF3_M_HasBackgroundImage	  -  (Mask) View has background image.

	VTF3_S_MaxRowsLimit	  -  (Shift) Limit the maximum rows returned for a Query View.

	VTF3_M_MaxRowsLimit	  -  (Mask) Limit the maximum rows returned for a Query View.


**Description :**

The Flags field of the VIEW_TABLE_FORMAT3 structure is a DWORD bit field of view table attributes.  The Shift flags specify the first bit position for a specific attribute.  The Mask flags specify the bit mask (which bits are used) for a specific attribute.


**See Also :**
[VIEW_TABLE_FORMAT3](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT3)
---
