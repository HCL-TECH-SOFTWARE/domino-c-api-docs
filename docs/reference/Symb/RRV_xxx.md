##### Symbolic Value : Note
##### RRV_xxx - Note ID size and deletion mask.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	RRV_ALIGNMENT	  -  Most typical RRV alignment.

	RRV_DELETED	  -  Indicates a deleted note.


**Description :**

The size of a Note ID to be used in a call to IDTableCreate().  The mask that is OR'd with all Note IDs (NOTEIDs) returned by NSFDbGetModifiedNoteTable().


**See Also :**
[IDCreateTable](/domino-c-api-docs/reference/Func/IDCreateTable)
[NSFDbGetModifiedNoteTable](/domino-c-api-docs/reference/Func/NSFDbGetModifiedNoteTable)
---
