##### Symbolic Value : Views
##### COLLATE_TYPE_xxx - COLLATE_DESCRIPTOR - keytype (Specifies how columns in a view are sorted.)
---
```
#include <nifcoll.h>
```

**Symbolic Values :**

	COLLATE_TYPE_KEY	  -  Collate by key in summary buffer

	COLLATE_TYPE_NOTEID	  -  Collate by note ID

	COLLATE_TYPE_TUMBLER	  -  Collate by "tumbler" summary key

	COLLATE_TYPE_CATEGORY	  -  Collate by "category" summary key


**Description :**

These are the possible values for the  keytype member of the COLLATE_DESCRIPTOR data structure.  The keytype structure member specifies the type of sorting that is done in the specified column in a view.


**See Also :**
[COLLATE_DESCRIPTOR](/domino-c-api-docs/reference/Data/COLLATE_DESCRIPTOR)
---
