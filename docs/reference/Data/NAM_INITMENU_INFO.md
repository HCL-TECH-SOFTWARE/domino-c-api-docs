##### Data Type : Menu Add-In
##### NAM_INITMENU_INFO - Contains information that can be used by a menu add-in program to determine whether to enable, disable, gray, check, etc. its menu item(s).
---
```
#include <addinmen.h>
```

**Definition :**
```
typedef struct
   {
   HMENU hMenu;         /* Handle of the Add-In PopUp menu. */
   NAM_CONTEXT_DATA Data;  /* Context specific data. */
   } NAM_INITMENU_INFO;
```

**Description :**

This structure contains information that can be used by a menu add-in program to determine whether to enable, disable, gray, check, etc. its menu item(s).<br>
<br>
The menu add-in receives this information when processing the NAMM_INITMENU message from Notes.


**See Also :**
[NAM_CONTEXT_DATA](/domino-c-api-docs/reference/Data/NAM_CONTEXT_DATA)
---
