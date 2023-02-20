##### Symbolic Value : Views
##### NIF_STAT_xxx - Description of codes used in certain view note items.
---
```
#include <nifcoll.h>
```
**Description :**

In $Totals view note item: 
	Use these flags to specify whether/which subtotals are to be kept for 
each summary buffer item. The $Totals item is a TYPE_TEXT_LIST item, where each 
member of the text list is a string which can be converted into one of the 
following codes by doing a "atoi" function on it. The order of the members of 
the text list MUST MATCH the order of the entries in the summary buffer, even 
if it means putting a blank string for a column which doesn't have any 
totalling.  All of these statistics are kept in each subindex header, and apply 
to all entries of that subindex AND ALL SUBINDEXES BELOW IT. 

In $VIEWFORMAT view note item: 
	Use these flags to set the SubtotalCode bits of the Flags2 member of a 
VIEW_COLUMN_FORMAT structure. 


**See Also :**
[VCF2_xxx](/reference/Symb/VCF2_xxx)
[VIEW_COLUMN_FORMAT](/reference/Data/VIEW_COLUMN_FORMAT)
---
