##### Data Type : Mixed 32/16-bit Model
##### NOTESMAIN - * OBSOLETE * Calling convention for NotesMain and AddInMain
---
##### #include <global.h>
**Description :**
***OBSOLETE - Included for backward compatibility only***

This macro defines the calling convention used for NotesMain and AddInMain 
programs.  In the mixed 32/16-bit model for OS/2 2.1, this macro will define 
NotesMain or AddInMain to be a 32-bit program using the "_Optlink" calling 
convention.  Under Windows and OS/2 1.x, the calling convention used is "FAR 
PASCAL".  On other platforms, this macro is null;  no special calling 
convention is used.
**Sample Usage :**
```
STATUS NOTESMAIN NotesMain (int argc, char * argv[])
{
    /* Here's the main module */
}
```
**See Also :**
[AddInMain](D:/md_files/AddInMain.md)
[LNPUBLIC](D:/md_files/LNPUBLIC.md)
[NOTESAPI](D:/md_files/NOTESAPI.md)
[NOTESAPICDECL](D:/md_files/NOTESAPICDECL.md)
[NOTESCALLBACK](D:/md_files/NOTESCALLBACK.md)
[NotesMain](D:/md_files/NotesMain.md)
---
