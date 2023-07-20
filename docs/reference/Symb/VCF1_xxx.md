##### Symbolic Value : Constants
##### VCF1_xxx - VIEW_COLUMN_FORMAT - Flags1
---
```
#include <viewfmt.h>
```

**Symbolic Values :**

	VCF1_S_Sort	  -  (Shift) Add column to sort.

	VCF1_M_Sort	  -  (Mask) Add column to sort.

	VCF1_S_SortCategorize	  -  (Shift) Make column a category.

	VCF1_M_SortCategorize	  -  (Mask) Make column a category.

	VCF1_S_SortDescending.	  -  (Shift) Sort in descending order (ascending if FALSE).

	VCF1_M_SortDescending	  -  (Mask) Sort in descending order (ascending if FALSE).

	VCF1_S_Hidden	  -  (Shift) Hidden column.

	VCF1_M_Hidden	  -  (Mask) Hidden column.

	VCF1_S_Response	  -  (Shift) Response column.

	VCF1_M_Response	  -  (Mask) Response column.

	VCF1_S_HideDetail	  -  (Shift) Do not show detail on subtotaled columns.

	VCF1_M_HideDetail	  -  (Mask) Do not show detail on subtotaled columns.

	VCF1_S_Icon	  -  (Shift) Display icon instead of text.

	VCF1_M_Icon	  -  (Mask) Display icon instead of text.

	VCF1_S_NoResize	  -  (Shift) Resizable at run time.

	VCF1_M_NoResize	  -  (Mask) Resizable at run time.

	VCF1_S_ResortAscending	  -  (Shift) Resortable in ascending order.

	VCF1_M_ResortAscending	  -  (Mask) Resortable in ascending order.

	VCF1_S_ResortDescending	  -  (Shift) Resortable in descending order.

	VCF1_M_ResortDescending	  -  (Mask) Resortable in descending order.

	VCF1_S_Twistie	  -  (Shift) Show twistie if expandable.

	VCF1_M_Twistie	  -  (Mask) Show twistie if expandable.

	VCF1_S_ResortToView	  -  (Shift) Resort to a view.

	VCF1_M_ResortToView	  -  (Mask) Resort to a view.

	VCF1_S_SecondResort	  -  (Shift) Secondary resort column set.

	VCF1_M_SecondResort	  -  (Mask) Secondary resort column set.

	VCF1_S_SecondResortDescending	  -  (Shift) Secondary column resort descending (ascending if clear).

	VCF1_M_SecondResortDescending	  -  (Mask) Secondary column resort descending (ascending if clear).

	VCF1_S_CaseInsensitiveSort	  -  OBSOLETE - replaced by VCF3_S_CaseSensitiveSortInV5

	VCF1_M_CaseInsensitiveSort	  -  OBSOLETE - replaced by VCF3_M_CaseSensitiveSortInV5

	VCF1_S_AccentInsensitiveSort	  -  OBSOLETE - replaced by VCF3_S_AccentSensitiveSortInV5

	VCF1_M_AccentInsensitiveSort	  -  OBSOLETE - replaced by VCF3_M_AccentSensitiveSortInV5


**Description :**

Possible optional values for the Flags1 member of the VIEW_COLUMN_FORMAT structure.  These values specify column attributes.


**See Also :**
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
---
