##### Symbolic Value : Folders
##### DESIGN_TYPE_xxx - Type of folder - shared or private.
---
##### #include <design.h>
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
[FolderCreate](D:/md_files/FolderCreate.md)
---
