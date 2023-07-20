##### Symbolic Value : Views
##### CDF_xxx - COLLATE_DESCRIPTOR - Flags
---
```
#include <nifcoll.h>
```

**Symbolic Values :**

	CDF_S_descending	  -  (Shift) Number of bits to shift to access the CDF_M_descending field.

	CDF_M_descending	  -  (Mask) True if descending; False if ascending order (default).

	CDF_M_ignoreprefixes	  -  If prefix list, then ignore for sorting.

	CDF_M_caseinsensitive	  -  * OBSOLETE * - see CDF_M_caseinsensitive_in_v5.
(Mask) If set, text compares are case-insensitive.

	CDF_M_accentinsensitive	  -  * OBSOLETE * - see CDF_M_accentinsensitive_in_v5.
(Mask) If set, text compares are accent-insensitive.

	CDF_M_permuted	  -  (Mask) If set, lists are permuted.

	CDF_M_permuted_pairwise	  -  (Mask) Qualifier if lists are permuted; if set, lists are pairwise permuted, otherwise lists are multiply permuted.

	CDF_M_flat_in_v5	  -  (Mask) If set, treat as permuted.

	CDF_M_casesensitive_in_v5	  -  (Mask) If set, text compares are case-sensitive.

	CDF_M_accentsensitive_in_v5	  -  (Mask) If set, text compares are accent-sensitive.


**Description :**

Bit field masks used to access components of the Flags field in the COLLATE_DESCRIPTOR structure.


**See Also :**
[COLLATE_DESCRIPTOR](/domino-c-api-docs/reference/Data/COLLATE_DESCRIPTOR)
---
