##### Data Type : Menu Add-In
##### NAM_COMMAND_INFO - Contains information that is sent to a menu add-in program.
---
```
#include <addinmen.h>
```

**Definition :**

typedef struct
   {
   HWND hNotesWnd;      /* Handle of Notes main window to use as 
                           parent. */
   WORD wMenuID;        /* DLL's ID number of selected menu item. */
   NAM_CONTEXT_DATA Data;  /* Context specific data */
   } NAM_COMMAND_INFO;

**Description :**

Contains information that is sent to a menu add-in program when the user selects one of its menu items.  The a menu add-in receives this information when processing the NAMM_COMMAND message from Notes.


**See Also :**
[NAM_CONTEXT_DATA](/domino-c-api-docs/reference/Data/NAM_CONTEXT_DATA)
[NAM_INIT_INFO](/domino-c-api-docs/reference/Data/NAM_INIT_INFO)
---
