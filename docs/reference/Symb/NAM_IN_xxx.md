##### Symbolic Value : Menu Add-In
##### NAM_IN_xxx - Notes menu add-in context flags.
---
```
#include <addinmen.h>
```

**Symbolic Values :**

	NAM_IN_DESK	  -  In the desktop.

	NAM_IN_VIEW	  -  In a view.

	NAM_IN_VIEW_DESIGN	  -  Designing a view.

	NAM_IN_EDIT_RO	  -  In a read-only document.

	NAM_IN_EDIT_RW	  -  In a document - edit mode.

	NAM_IN_EDIT_DESIGN	  -  Designing a document.


**Description :**

These flags specify the current context when a menu add-in program is invoked.  This information is received by the menu add-in in the NAM_CONTEXT_DATA structure when processing the NAMM_COMMAND message from Notes.


**See Also :**
[NAM_CONTEXT_DATA](/domino-c-api-docs/reference/Data/NAM_CONTEXT_DATA)
[NAM_COMMAND_INFO](/domino-c-api-docs/reference/Data/NAM_COMMAND_INFO)
[NAMM_xxx](/domino-c-api-docs/reference/Symb/NAMM_xxx)
---
