##### Data Type : Mixed 32/16-bit Model
##### NOTESAPICDECL - * OBSOLETE * "C" calling convention for Notes API Functions
---
```
#include <global.h>
```
**Description :**

***OBSOLETE - Included for backward compatibility only***

This macro defines the calling convention used for Notes API functions that 
have a variable number of arguments.  Normally, this macro is only used in the 
API header files, not in application code.  In the mixed 32/16-bit model for 
OS/2 2.1, this macro specifies that Notes API functions use the 16-bit "_Far16 
_Cdecl" calling convention.  Under Windows and OS/2 1.x, the calling convention 
used is "FAR cdecl".  On other platforms, this macro is null;  no special 
calling convention is used.

Note that functions that allow a variable number of arguments have no way of 
specifying the types of those arguments for the compiler.  In the mixed 
32/16-bit model, data in the application program is usually 32 bits long, while 
the Notes API functions require 16-bit arguments.  This requires using a 
typecast to ensure that the value is converted.

**Sample Usage :**
```
Declaration in addin.h:

    void NOTESAPICDECL AddInSetStatus (char NOTESPTR String, ...);

Usage example:

    #include <global.h>
    #include <addin.h>

    AddInSetStatus (FORMAT_RESOURCE,
        (char NOTESPTR) "Current Status");
```
**See Also :**
[LNVARARGS](/domino-c-api-docs/reference/Symb/LNVARARGS)
[NOTESAPI](/domino-c-api-docs/reference/Data/NOTESAPI)
[NOTESCALLBACK](/domino-c-api-docs/reference/Data/NOTESCALLBACK)
[NotesMain](/domino-c-api-docs/reference/Func/NotesMain)
---
