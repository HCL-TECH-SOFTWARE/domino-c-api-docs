##### Symbolic Value : Constants
##### VCF2_xxx - VIEW_COLUMN_FORMAT - Flags2
---
```
#include <viewfmt.h>
```

**Symbolic Values :**

	VCF2_S_DisplayAlignment	  -  (Shift) Display alignment (see VIEW_COL_ALIGN_xxx).

	VCF2_M_DisplayAlignment	  -  (Mask) Display alignment (see VIEW_COL_ALIGN_xxx).

	VCF2_S_SubtotalCode	  -  (Shift) Subtotal code (see NIF_STAT_xxx).

	VCF2_M_SubtotalCode	  -  (Mask) Subtotal code (see NIF_STAT_xxx).

	VCF2_S_HeaderAlignment	  -  (Shift) Header alignment (see VIEW_COL_ALIGN_xxx).

	VCF2_M_HeaderAlignment	  -  (Mask) Header alignment (see VIEW_COL_ALIGN_xxx).

	VCF2_S_SortPermute	  -  (Shift) Make column permuted if multi-valued.

	VCF2_M_SortPermute	  -  (Mask) Make column permuted if multi-valued.

	VCF2_S_SecondResortUniqueSort	  -  (Shift) Secondary resort column props different from column def.

	VCF2_M_SecondResortUniqueSort	  -  (Mask) Secondary resort column props different from column def.

	VCF2_S_SecondResortCategorized	  -  (Shift) Secondary resort column categorized.

	VCF2_M_SecondResortCategorized	  -  (Mask) Secondary resort column categorized.

	VCF2_S_SecondResortPermute	  -  (Shift) Secondary resort column permuted.

	VCF2_M_SecondResortPermute	  -  (Mask) Secondary resort column permuted.

	VCF2_S_SecondResortPermutePair	  -  (Shift) Secondary resort column pairwise permuted.

	VCF2_M_SecondResortPermutePair	  -  (Mask) Secondary resort column pairwise permuted.

	VCF2_S_ShowValuesAsLinks	  -  (Shift) Show values as links when viewed by web browsers.

	VCF2_M_ShowValuesAsLinks	  -  (Mask) Show values as links when viewed by web browsers.

	VCF2_S_DisplayReadingOrder	  -  (Shift) Display reading order (see VIEW_COL_xxx(2)).

	VCF2_M_DisplayReadingOrder	  -  (Mask) Display reading order (see VIEW_COL_xxx(2)).

	VCF2_S_HeaderReadingOrder	  -  (Shift) Header reading order (see VIEW_COL_xxx(2)).

	VCF2_M_HeaderReadingOrder	  -  (Mask) Header reading order (see VIEW_COL_xxx(2)).


**Description :**

The Flags2 field of the VIEW_COLUMN_FORMAT structure is a WORD bit field of view column attributes.  The Shift flags specify the first bit position for a specific attribute.  The Mask flags specify the bit mask (which bits are used) for a specific attribute.


**See Also :**
[NIF_STAT_xxx](/domino-c-api-docs/reference/Symb/NIF_STAT_xxx)
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
[VIEW_COL_ALIGN_xxx](/domino-c-api-docs/reference/Symb/VIEW_COL_ALIGN_xxx)
---
