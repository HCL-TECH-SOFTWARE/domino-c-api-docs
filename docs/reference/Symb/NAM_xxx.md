##### Symbolic Value : Menu Add-In
##### NAM_xxx - Return values for the entry point of a Notes menu add-in program.
---
```
#include <addinmen.h>
```

**Symbolic Values :**

	NAM_NOERROR	  -  Return value for NAMM_INITMENU, NAMM_COMMAND, and NAMM_TERM message - no error.

	NAM_INIT_CONTINUE	  -  Possible return value for NAMM_INIT message. Requests Notes to send NAM_INIT again so that the menu add-in can add another menu item.

	NAM_INIT_STOP	  -  Possible return value for NAMM_INIT message. Tells Notes that this menu add-in program has no more menu items to add.


**Description :**

These are the possible return values for the entry point of a Notes menu add-in program.


**See Also :**
[NAMM_xxx](/domino-c-api-docs/reference/Symb/NAMM_xxx)
---
