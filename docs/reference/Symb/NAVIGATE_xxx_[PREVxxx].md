##### Symbolic Value : Views
##### NAVIGATE_xxx [PREVxxx] - How NIFReadEntries steps through a collection.
---
```
#include <nif.h>
```

**Symbolic Values :**

	NAVIGATE_PREV	  -  Previous entry over entire tree (opposite order of PREORDER).

	NAVIGATE_PREV_PEER	  -  Previous node at our level.

	NAVIGATE_PREV_MAIN	  -  CURRENT_MAIN, then PREV_PEER only if already there.

	NAVIGATE_PREV_PARENT	  -  PARENT, then PREV_PEER.

	NAVIGATE_PREV_UNREAD	  -  PREV, but only "unread" entries.

	NAVIGATE_PREV_UNREAD_MAIN	  -  Previous unread main.

	NAVIGATE_PREV_SELECTED	  -  PREV, but only "selected" entries.

	NAVIGATE_PREV_SELECTED_MAIN	  -  Previous selected main.

	NAVIGATE_PREV_EXPANDED	  -  PREV, but only "expanded" entries.

	NAVIGATE_PREV_EXPANDED_UNREAD	  -  PREV, but only "expanded" AND "unread" entries.

	NAVIGATE_PREV_EXPANDED_SELECTED	  -  PREV, but only "expanded" AND "selected" entries.

	NAVIGATE_PREV_EXPANDED_CATEGORY	  -  PREV, but only "expanded" AND "category" entries.

	NAVIGATE_PREV_EXP_NONCATEGORY	  -  PREV, but only "expanded" "non-category" entries.

	NAVIGATE_PREV_HIT	  -  PREV, but only FTSearch "hit" entries (in the SAME ORDER as the hit's relevance ranking).

	NAVIGATE_PREV_SELECTED_HIT	  -  PREV, but only "selected" and FTSearch "hit" entries (in the SAME ORDER as the hit's relevance ranking).

	NAVIGATE_PREV_UNREAD_HIT	  -  PREV, but only "unread" and FTSearch "hit" entries (in the SAME ORDER as the hit's relevance ranking).

	NAVIGATE_PREV_CATEGORY	  -  PREV, but only "category" entries.

	NAVIGATE_PREV_NONCATEGORY	  -  PREV, but only "non-category" entries.


**Description :**

These flags control how NIFReadEntries steps through a collection. The flags are used to control both the order in which NIFReadEntries: skips notes in a collection before reading any notes, and navigates the collection while it is being read.


**See Also :**
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
