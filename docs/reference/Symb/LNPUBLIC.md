##### Symbolic Value : Standard
##### LNPUBLIC - Calling convention for IBM C API functions for Domino and Notes.
---
```
#include <global.h>
```

**Symbolic Values :**



**Definition :**
```
#if !defined(OS2)

   #define LNPUBLIC FAR PASCAL

#else

   /* OS/2 requires a separate macro because the ordering of function
      modifiers for function pointers is different.  This prevents us
      from inserting _System in a uniform place (e.g. a replacement
      for PASCAL). */

   #define LNPUBLIC _System

#endif
```

**Description :**

Calling convention for IBM C API functions for Domino and Notes


**Sample Usage :**
```
STATUS LNPUBLIC NotesInitExtended (int argc, char NOTESPTR NOTESPTR argv);
```

**See Also :**
[LNCALLBACK](/domino-c-api-docs/reference/Data/LNCALLBACK)
[LNCALLBACKPTR](/domino-c-api-docs/reference/Data/LNCALLBACKPTR)
[LNVARARGS](/domino-c-api-docs/reference/Symb/LNVARARGS)
[NOTESAPI](/domino-c-api-docs/reference/Data/NOTESAPI)
[NOTESMAIN](/domino-c-api-docs/reference/Data/NOTESMAIN)
---
