##### Data Type : Menu Add-In
##### NAM_CONTEXT_DATA - Contains import/export information.
---
```
#include <addinmen.h>
```

**Definition :**
```
typedef struct
   {
   FLAG Context:3;    /* Desk, View, Editor R/W, Editor R/O */
   FLAG fCanExport:1; /* TRUE if the add-in can perform an export.*/
   FLAG fCanImport:1; /* TRUE if the add-in can request an import.*/
   union
      {
      EDITIXDATA Edit;
      VIEWIXDATA View;
      } IXData;
   } NAM_CONTEXT_DATA;
```

**Description :**

This structure provides import/export data to a menu add-in program.  The Context field of indicates the Notes context when the menu item was selected.  It can take one of the following values:<br>
     NAM_IN_DESK                        In the desktop.<br>
     NAM_IN_VIEW                         In a view.<br>
     NAM_IN_VIEW_DESIGN     Designing a view.<br>
     NAM_IN_EDIT_RO                In a read only document.<br>
     NAM_IN_EDIT_RW               In a document - edit mode.<br>
     NAM_IN_EDIT_DESIGN      Designing a document.<br>
<br>
The a menu add-in receives this information when processing the NAMM_COMMAND message from Notes.<br>



**See Also :**
[NAM_xxx](/domino-c-api-docs/reference/Symb/NAM_xxx)
[NAM_IN_xxx](/domino-c-api-docs/reference/Symb/NAM_IN_xxx)
[EDITIXDATA](/domino-c-api-docs/reference/Data/EDITIXDATA)
[EDITIMPORTDATA](/domino-c-api-docs/reference/Data/EDITIMPORTDATA)
[EDITEXPORTDATA](/domino-c-api-docs/reference/Data/EDITEXPORTDATA)
[VIEWIXDATA](/domino-c-api-docs/reference/Data/VIEWIXDATA)
[NAM_COMMAND_INFO](/domino-c-api-docs/reference/Data/NAM_COMMAND_INFO)
---
