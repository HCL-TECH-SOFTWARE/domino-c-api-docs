##### Data Type : Composite Data
##### ActionRoutinePtr - Callback function pointer used in EnumCompositeBuffer and EnumCompositeFile.
---
```
#include <ods.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR ActionRoutinePtr)(
   char far *,
   WORD,
   DWORD,
   void far *);
```

**Description :**

This data structure defines the syntax of the user-defined callback function called by EnumCompositeBuffer and EnumCompositeFile.  The specified callback function is called for each CD record found in an item.


**See Also :**
[EnumCompositeBuffer](/domino-c-api-docs/reference/Func/EnumCompositeBuffer)
[EnumCompositeFile](/domino-c-api-docs/reference/Func/EnumCompositeFile)
---
