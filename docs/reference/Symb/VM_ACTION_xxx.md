##### Symbolic Value : Navigators
##### VM_ACTION_xxx - Navigator action codes.
---
```
#include <vmods.h>
```

**Symbolic Values :**

	VM_ACTION_NONE	  -  Take no action.

	VM_ACTION_SWITCHVIEW	  -  Open a view.

	VM_ACTION_SWITCHNAV	  -  Open another Navigator.

	VM_ACTION_ALIAS_FOLDER	  -  Serve as an alias for a Folder.

	VM_ACTION_GOTO_LINK	  -  Open a link.

	VM_ACTION_RUNSCRIPT	  -  Run a LotusScript script.

	VM_ACTION_RUNFORMULA	  -  Run a formula.

	VM_ACTION_GOTO_URL	  -  Go to a URL


**Description :**

These codes identify the action to be performed when the user selects a graphical element in a Navigator.  These values are stored in the ClickAction field of the VIEWMAP_ACTION_RECORD.


**See Also :**
[VIEWMAP_ACTION_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_ACTION_RECORD)
---
