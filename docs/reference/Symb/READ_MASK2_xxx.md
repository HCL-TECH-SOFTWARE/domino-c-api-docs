##### Symbolic Value : Views
##### READ_MASK2_xxx - Additional information returned by NIFReadEntriesExt2.
---
```
#include <nif.h>
```

**Symbolic Values :**

	READ_MASK2_TO_JSON	  -  returns output from NIFReadEntriesExt2 in the form of JSON.	

**Description :**

These flags control what information is returned by NIFReadEntriesExt2 for each note that is found. All of the information requested is returned in the buffer that NIFReadEntriesExt2 creates.
<br>
The return buffer is in either structure or JSON format.

**See Also :**
[ITEM_TABLE](/domino-c-api-docs/reference/Data/ITEM_TABLE)
[ITEM_VALUE_TABLE](/domino-c-api-docs/reference/Data/ITEM_VALUE_TABLE)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
