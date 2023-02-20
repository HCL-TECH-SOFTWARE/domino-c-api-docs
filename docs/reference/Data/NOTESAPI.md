##### Data Type : Mixed 32/16-bit Model
##### NOTESAPI - * OBSOLETE * Calling convention for Notes API Functions
---
```
#include <global.h>
```
**Description :**

***OBSOLETE - Included for backward compatibility only***

This macro defines the calling convention used for Notes API functions that 
have a fixed number of arguments.  Normally, this macro is only used in the API 
header files, not in application code.  In the mixed 32/16-bit model for OS/2 
2.1, this macro specifies that Notes API functions use the 16-bit "_Far16 
_Pascal" calling convention.  Under Windows and OS/2 1.x, the calling 
convention used is "FAR PASCAL".  On other platforms, this macro is null;  no 
special calling convention is used.

**Sample Usage :**
```
STATUS NOTESAPI NotesInitExtended (int argc, char NOTESPTR NOTESPTR argv);
```
**See Also :**
[LNPUBLIC](/reference/Symb/LNPUBLIC)
[NOTESAPICDECL](/reference/Data/NOTESAPICDECL)
[NOTESCALLBACK](/reference/Data/NOTESCALLBACK)
[NotesMain](/reference/Func/NotesMain)
---