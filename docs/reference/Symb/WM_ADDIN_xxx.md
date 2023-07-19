##### Symbolic Value : Add-In DLL
##### WM_ADDIN_xxx - Messages a menu add-In function may send to Notes
---
```
#include <addinmen.h>
```

**Symbolic Values :**

	WM_ADDIN_FIRST	  -  Menu add-in message identifier. This symbol is used in the definition of the messages a menu add-in may send to Notes. It is not to be explicitly used by the menu add-in program.

	WM_ADDIN_REFRESH	  -  Tells Notes to refresh the current view.

	WM_ADDIN_IMPORT	  -  Tells Notes to import to the editor the CD scratch file specified in the context block.


**Description :**

Identifiers that specify messages a menu add-in function may send to the Notes main window. Use these symbols when calling SendMessage under Windows to specify what message to send to the Notes window. These messages request Notes to take a particular action. Menu add-in functions may send these messages to the Notes main window when processing the NAMM_COMMAND message.


**See Also :**
[NAMM_xxx](/domino-c-api-docs/reference/Symb/NAMM_xxx)
---
