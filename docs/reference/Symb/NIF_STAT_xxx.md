##### Symbolic Value : Views
##### NIF_STAT_xxx - Description of codes used in certain view note items.
---
```
#include <nifcoll.h>
```

**Symbolic Values :**

	NIF_STAT_NONE	  -  No subtotalling.

	NIF_STAT_TOTAL	  -  Total of values in subtree.

	NIF_STAT_AVG_PER_CHILD	  -  Total / # direct entries in parent's index (1 level only below parent).

	NIF_STAT_PCT_OVERALL	  -  Total / total of values in entire index.

	NIF_STAT_PCT_PARENT	  -  Total / total of values in parent's index.

	NIF_STAT_AVG_PER_ENTRY	  -  Total / # descendants in parent's index (all levels below parent).

	NIF_STAT_AVERAGE	  -  Obsolete symbol.


**Description :**

<br>
In $Totals view note item: <br>
	Use these flags to specify whether/which subtotals are to be kept for each summary buffer item. The $Totals item is a TYPE_TEXT_LIST item, where each member of the text list is a string which can be converted into one of the following codes by doing a &quot;atoi&quot; function on it. The order of the members of the text list MUST MATCH the order of the entries in the summary buffer, even if it means putting a blank string for a column which doesn't have any totalling.  All of these statistics are kept in each subindex header, and apply to all entries of that subindex AND ALL SUBINDEXES BELOW IT. <br>
<br>
In $VIEWFORMAT view note item: <br>
	Use these flags to set the SubtotalCode bits of the Flags2 member of a VIEW_COLUMN_FORMAT structure. 


**See Also :**
[VCF2_xxx](/domino-c-api-docs/reference/Symb/VCF2_xxx)
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
---
