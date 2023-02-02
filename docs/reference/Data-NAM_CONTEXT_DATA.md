##### Data Type : Menu Add-In
##### NAM_CONTEXT_DATA - Contains import/export information.
---
##### #include <addinmen.h>
**Description :**
This structure provides import/export data to a menu add-in program.  The 
Context field of indicates the Notes context when the menu item was selected.  
It can take one of the following values:
     NAM_IN_DESK                        In the desktop.
     NAM_IN_VIEW                         In a view.
     NAM_IN_VIEW_DESIGN     Designing a view.
     NAM_IN_EDIT_RO                In a read only document.
     NAM_IN_EDIT_RW               In a document - edit mode.
     NAM_IN_EDIT_DESIGN      Designing a document.

The a menu add-in receives this information when processing the NAMM_COMMAND 
message from Notes.

**See Also :**
[NAM_xxx](D:/md_files/NAM_xxx.md)
[NAM_IN_xxx](D:/md_files/NAM_IN_xxx.md)
[EDITIXDATA](D:/md_files/EDITIXDATA.md)
[EDITIMPORTDATA](D:/md_files/EDITIMPORTDATA.md)
[EDITEXPORTDATA](D:/md_files/EDITEXPORTDATA.md)
[VIEWIXDATA](D:/md_files/VIEWIXDATA.md)
[NAM_COMMAND_INFO](D:/md_files/NAM_COMMAND_INFO.md)
---
