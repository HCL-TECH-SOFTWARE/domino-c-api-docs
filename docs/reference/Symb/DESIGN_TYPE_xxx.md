##### Symbolic Value : Folders
##### DESIGN_TYPE_xxx - Type of folder - shared or private.
---
```
#include <design.h>
```

**Symbolic Values :**

	DESIGN_TYPE_SHARED	  -  Note is shared. Shared notes are always stored in the database. They are never stored in the desktop file.

	DESIGN_TYPE_PRIVATE_DATABASE	  -  Note is private and is stored in the database rather than in the desktop file.


**Description :**

These symbolic constants describe the type of folder being created.


**Sample Usage :**
```
if (error = FolderCreate (hDB2, NULLHANDLE, FormatNoteID, hDB1, 
                          "API Folder", MAXWORD,
                          DESIGN_TYPE_PRIVATE_DATABASE,
                          0L, &FNoteID))
```

**See Also :**
[FolderCreate](/domino-c-api-docs/reference/Func/FolderCreate)
---
