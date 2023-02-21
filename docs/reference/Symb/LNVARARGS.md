##### Symbolic Value : Standard
##### LNVARARGS - "C" calling convention for IBM C API functions for Domino and Notes.
---
```
#include <global.h>
```
**Description :**

This macro defines the calling convention used for  IBM C API functions for 
Domino and Notes that have a variable number of arguments.

**Sample Usage :**
```
Declaration in addin.h:

    void LNVARARGS AddInSetStatus (char far * String, ...);

Usage example:

    #include <global.h>
    #include <addin.h>

    AddInSetStatus (FORMAT_RESOURCE,
        (char far *) "Current Status");
```
**See Also :**
[LNCALLBACK](/domino-c-api-docs/reference/Data/LNCALLBACK)
[LNPUBLIC](/domino-c-api-docs/reference/Symb/LNPUBLIC)
[NOTESAPICDECL](/domino-c-api-docs/reference/Data/NOTESAPICDECL)
---
