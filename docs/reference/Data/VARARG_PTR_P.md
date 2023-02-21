##### Data Type : Extension Manager
##### VARARG_PTR_P - Pointer to a variable argument list.
---
```
#include <global.h>
```
**Description :**

Pointer to a variable argument list.

Platforms that strictly comply to the C standard do not allow passing of 
variable argument lists by reference using '&' and '*' operators because the 
standard states that you may get undetermined results.  However, you are 
allowed to pass a variable argument list without these operators.  On Linux for 
zSeries, whenever you pass a variable argument list the contents will always be 
modified upon returning from the function passing it in as a parameter 
(assuming some function below accesses the list.)  For these types of 
platforms, the following macros are defined to just pass the list without using 
the '&' operator.  All platforms can still use a variable argument list as a 
pointer by simply using the VARARG_PTR_P type.

#if defined(ZLINUX)
typedef VARARG_PTR VARARG_PTR_P;
#define VARARG_ADDR(_AAP) _AAP
#define VARARG_DEREF(_AAP) _AAP
#define VARARG_COPY __va_copy
#else
typedef VARARG_PTR * VARARG_PTR_P;
#define VARARG_ADDR(_AAP) &_AAP
#define VARARG_DEREF(_AAP) *_AAP
#define VARARG_COPY(dest, src) (dest)=(src)
#endif

**See Also :**
[VARARG_ADDR](/domino-c-api-docs/reference/Func/VARARG_ADDR)
[VARARG_COPY](/domino-c-api-docs/reference/Func/VARARG_COPY)
[VARARG_DEREF](/domino-c-api-docs/reference/Func/VARARG_DEREF)
[VARARG_GET](/domino-c-api-docs/reference/Func/VARARG_GET)
[VARARG_PEEK](/domino-c-api-docs/reference/Func/VARARG_PEEK)
[VARARG_PTR](/domino-c-api-docs/reference/Data/VARARG_PTR)
[VARARG_START](/domino-c-api-docs/reference/Func/VARARG_START)
---
