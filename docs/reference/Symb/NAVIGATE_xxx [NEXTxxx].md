##### Symbolic Value : Views
##### NAVIGATE_xxx [NEXTxxx] - How NIFReadEntries steps through a collection.
---
```
#include <nif.h>
```

**Symbolic Values :**

	NAVIGATE_NEXT	  -  Next entry over entire tree (parent first, then children,...).

	NAVIGATE_NEXT_PEER	  -  Next node at our level.

	NAVIGATE_NEXT_MAIN	  -  CURRENT_MAIN, then NEXT_PEER.

	NAVIGATE_NEXT_PARENT	  -  PARENT, then NEXT_PEER.

	NAVIGATE_NEXT_UNREAD	  -  NEXT, but only "unread" entries.

	NAVIGATE_NEXT_UNREAD_MAIN	  -  NEXT_UNREAD, but stop at main note also.

	NAVIGATE_NEXT_SELECTED	  -  NEXT, but only "selected" entries.

	NAVIGATE_NEXT_SELECTED_MAIN	  -  Next selected main.

	NAVIGATE_NEXT_EXPANDED	  -  NEXT, but only "expanded" entries.

	NAVIGATE_NEXT_EXPANDED_UNREAD	  -  NEXT, but only "expanded" AND "unread" entries.

	NAVIGATE_NEXT_EXPANDED_SELECTED	  -  NEXT, but only "expanded" AND "selected" entries.

	NAVIGATE_NEXT_EXPANDED_CATEGORY	  -  NEXT, but only "expanded" AND "category" entries.

	NAVIGATE_NEXT_EXP_NONCATEGORY	  -  NEXT, but only "expanded" "non-category" entries.

	NAVIGATE_NEXT_HIT	  -  NEXT, but only FTSearch "hit" entries (in the SAME ORDER as the hit's relevance ranking).

	NAVIGATE_NEXT_SELECTED_HIT	  -  NEXT, but only "selected" and FTSearch "hit" entries (in the SAME ORDER as the hit's relevance ranking).

	NAVIGATE_NEXT_UNREAD_HIT	  -  NEXT, but only "unread" and FTSearch "hit" entries (in the SAME ORDER as the hit's relevance ranking).

	NAVIGATE_NEXT_CATEGORY	  -  NEXT, but only "category" entries.

	NAVIGATE_NEXT_NONCATEGORY	  -  NEXT, but only "non-category" entries.


**Description :**

These flags control how NIFReadEntries steps through a collection. The flags are used to control both the order in which NIFReadEntries: skips notes in a collection before reading any notes, and navigates the collection while it is being read.


**See Also :**
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
