##### Data Type : Extension Manager
##### VARARG_PTR_P - Pointer to a variable argument list.
---
```
#include <global.h>
```

**Definition :**



**Description :**

Pointer to a variable argument list.
<ul><br>
<br>
Platforms that strictly comply to the C standard do not allow passing of variable argument lists by reference using '&amp;' and '*' operators because the standard states that you may get undetermined results.  However, you are allowed to pass a variable argument list without these operators.  On Linux for zSeries, whenever you pass a variable argument list the contents will always be modified upon returning from the function passing it in as a parameter (assuming some function below accesses the list.)  For these types of platforms, the following macros are defined to just pass the list without using the '&amp;' operator.  All platforms can still use a variable argument list as a pointer by simply using the VARARG_PTR_P type.<br>
<br>
#if defined(ZLINUX)<br>
typedef VARARG_PTR VARARG_PTR_P;<br>
#define VARARG_ADDR(_AAP) _AAP<br>
#define VARARG_DEREF(_AAP) _AAP<br>
#define VARARG_COPY __va_copy<br>
#else<br>
typedef VARARG_PTR * VARARG_PTR_P;<br>
#define VARARG_ADDR(_AAP) &amp;_AAP<br>
#define VARARG_DEREF(_AAP) *_AAP<br>
#define VARARG_COPY(dest, src) (dest)=(src)<br>
#endif</ul>



**See Also :**
[VARARG_ADDR](/domino-c-api-docs/reference/Func/VARARG_ADDR)
[VARARG_COPY](/domino-c-api-docs/reference/Func/VARARG_COPY)
[VARARG_DEREF](/domino-c-api-docs/reference/Func/VARARG_DEREF)
[VARARG_GET](/domino-c-api-docs/reference/Func/VARARG_GET)
[VARARG_PEEK](/domino-c-api-docs/reference/Func/VARARG_PEEK)
[VARARG_PTR](/domino-c-api-docs/reference/Data/VARARG_PTR)
[VARARG_START](/domino-c-api-docs/reference/Func/VARARG_START)
---
