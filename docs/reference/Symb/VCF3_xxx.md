##### Symbolic Value : Constants
##### VCF3_xxx - VIEW_COLUMN_FORMAT2 - Flags3
---
```
#include <viewfmt.h>
```

**Symbolic Values :**

	VCF3_S_FlatInV5	  -  (Shift) View is flat in V5 or greater.

	VCF3_M_FlatInV5	  -  (Mask) View is flat in V5 or greater.

	VCF3_S_CaseSensitiveSortInV5	  -  (Shift) Case Sensitive sorting.

	VCF3_M_CaseSensitiveSortInV5	  -  (Mask) Case Sensitive sorting.

	VCF3_S_AccentSensitiveSortInV5	  -  (Shift) Accent Sensitive sorting.

	VCF3_M_AccentSensitiveSortInV5	  -  (Mask) Accent Sensitive sorting.

	VCF3_S_HideWhenFormula	  -  (Shift) Column has hide/when formula set.

	VCF3_M_HideWhenFormula	  -  (Mask) Column has hide/when formula set.

	VCF3_S_TwistieResource	  -  (Shift) Column has twistie resource.

	VCF3_M_TwistieResource	  -  (Mask) Column has twistie resource.

	VCF3_S_Color	  -  (Shift) Column value to be used as a color for this entry.

	VCF3_M_Color	  -  (Mask) Column value to be used as a color for this entry.

	VCF3_ExtDate	  -  Column has extended date info.

	VCF3_NumberFormat	  -  Column has extended number format.

	VCF3_S_IsColumnEditable	  -  (Shift) Can this column be edited.

	VCF3_M_IsColumnEditable	  -  (Mask) Can this column be edited.

	VCF3_S_UserDefinableColor	  -  (Shift) User definable color.

	VCF3_M_UserDefinableColor	  -  (Mask) User definable color.

	VCF3_S_HideInR5	  -  (Shift) Column has hide/when formula set and needs to be hidden in R5 or before.

	VCF3_M_HideInR5	  -  (Mask) Column has hide/when formula set and needs to be hidden in R5 or before.

	VCF3_S_NamesFormat	  -  (Shift) Column has extended names format.

	VCF3_M_NamesFormat	  -  (Mask) Column has extended names format.

	VCF3_S_HideColumnTitle	  -  (Shift) Hide column title from display, but not from customization.

	VCF3_M_HideColumnTitle	  -  (Mask) Hide column title from display, but not from customization.

	VCF3_S_IsSharedColumn	  -  (Shift) Is this a shared column?

	VCF3_M_IsSharedColumn	  -  (Mask) Is this a shared column?

	VCF3_S_UseSharedColumnFormulaOnly	  -  (Shift) Use only the formula from shared column - let use modify everything else.

	VCF3_M_UseSharedColumnFormulaOnly	  -  (Mask) Use only the formula from shared column - let use modify everything else.


**Description :**

The Flags3 field of the VIEW_COLUMN_FORMAT2 structure is a WORD bit field of view attributes.  The Shift flags specify the first bit position for a specific attribute.  The Mask flags specify the bit mask (which bits are used) for a specific attribute.


**See Also :**
[VIEW_COLUMN_FORMAT2](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT2)
---
