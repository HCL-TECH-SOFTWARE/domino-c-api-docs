##### Data Type : Menu Add-In
##### NAMPROC - Menu add-in program's entry point.
---
```
#include <addinmen.h>
```

**Definition :**
```
typedef NAMRESULT (LNCALLBACKPTR NAMPROC)(
   WORD Command,
   void far *pParam);
```

**Description :**

This is the data type of a menu add-in program's entry point


**See Also :**
[NAMRESULT](/domino-c-api-docs/reference/Data/NAMRESULT)
[NAMM_xxx](/domino-c-api-docs/reference/Symb/NAMM_xxx)
---
