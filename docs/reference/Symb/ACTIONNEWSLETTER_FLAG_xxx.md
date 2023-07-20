##### Symbolic Value : Agents
##### ACTIONNEWSLETTER_FLAG_xxx - Option flags for CDACTIONNEWSLETTER record.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	ACTIONNEWSLETTER_FLAG_SUMMARY	  -  Include a summary of each document.

	ACTIONNEWSLETTER_FLAG_GATHER	  -  Gather at least the number of documents specified in the dwGather field of the CDACTIONNEWSLETTER structure before mailing.

	ACTIONNEWSLETTER_FLAG_INCLUDEALL	  -  Include all notes when mailing out multiple notes.


**Description :**

These flags specify options for the Newsletter action record in a TYPE_ACTION item.  These flags are stored in the dwFlags field of the CDACTIONNEWSLETTER structure.


**See Also :**
[CDACTIONNEWSLETTER](/domino-c-api-docs/reference/Data/CDACTIONNEWSLETTER)
---
