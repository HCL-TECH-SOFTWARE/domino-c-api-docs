##### Symbolic Value : Resource Definition
##### debugtext - Assign an error code number to a text string.
---
```
#include <globerr.h>
```

**Symbolic Values :**



**Description :**

Assigns the given error code to the given text string.  When language compiling, the macro actually amounts to nothing more than a comment.  When resource compiling a module (RC), the macro is used to map error code numbers to a corresponding text string.
<ul><br>
<br>
Prior to Release 4.5, an alternative form was defined due to a compiler bug in MPW C.  The compiler generated an error when a macro evaluated to nothing and is followed by another #define.<br>
<br>
<br>
<br>
/* &quot;debugtext&quot; designates DEBUG-only messages. This is not to be<br>
 translated and never shown to a user. */<br>
<br>
#define debugtext(code,text)<br>
</ul>



**Sample Usage :**
```
#define ERR_POOL_FREE_CHAIN   PKG_MISC+26
 debugtext(ERR_POOL_FREE_CHAIN, "Invalid pool free chain")
#define ERR_LOCK_POOL_TWICE   PKG_MISC+27
 debugtext(ERR_LOCK_POOL_TWICE, "Attempt to lock twice using same pool lock")
#define ERR_TOO_MANY_LOCKS   PKG_MISC+28
 debugtext(ERR_TOO_MANY_LOCKS,  "Too many locks on pool")
```

**See Also :**
[AddInFormatError](/domino-c-api-docs/reference/Func/AddInFormatError)
[AddInLogError](/domino-c-api-docs/reference/Func/AddInLogError)
[AddInSetStatus](/domino-c-api-docs/reference/Func/AddInSetStatus)
[PKG_xxx](/domino-c-api-docs/reference/Symb/PKG_xxx)
[OSLoadString](/domino-c-api-docs/reference/Func/OSLoadString)
---
