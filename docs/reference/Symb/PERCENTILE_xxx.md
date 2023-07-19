##### Symbolic Value : Search
##### PERCENTILE_xxx - Indices into percentile key table
---
```
#include <nif.h>
```

**Symbolic Values :**

	PERCENTILE_0	  -  0: Table entry for first key in collection

	PERCENTILE_10	  -  1: Table entry for first 1/10 of collection

	PERCENTILE_20	  -  2: Table entry for second 1/10 of collection

	PERCENTILE_30	  -  3: Table entry for third 1/10 of collection

	PERCENTILE_40	  -  4: Table entry for fourth 1/10 of collection

	PERCENTILE_50	  -  5: Table entry for the first half of a collection

	PERCENTILE_60	  -  6: Table entry for sixth 1/10 of collection

	PERCENTILE_70	  -  7: Table entry for seventh 1/10 of collection

	PERCENTILE_80	  -  8: Table entry for eighth 1/10 of collection

	PERCENTILE_90	  -  9: Table entry for ninth 1/10 of collection 1/10 of collection

	PERCENTILE_100	  -  10: Table entry for last key in collection


**Description :**

Keys in a COLLECTIONDATA structure are divided into percentiles - divisions corresponding to one-tenth of the total range of keys - and a table of the keys marking the divisions is returned with that structure.  These constants are provided for indexing into the table.


**See Also :**
[COLLECTIONDATA](/domino-c-api-docs/reference/Data/COLLECTIONDATA)
[PERCENTILE_COUNT](/domino-c-api-docs/reference/Symb/PERCENTILE_COUNT)
---
