##### Symbolic Value : Resource Definition
##### apitext - Assign an error code number to a text string.
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
/* &quot;apitext&quot; designates API-only messages. This could be translated<br>
 (for foreign API programmers) but NEVER shown to a user. */<br>
<br>
#define apitext(code,text)<br>
</ul>



**See Also :**
[errortext](/domino-c-api-docs/reference/Symb/errortext)
[internaltext](/domino-c-api-docs/reference/Symb/internaltext)
[helptext](/domino-c-api-docs/reference/Symb/helptext)
[stringtext](/domino-c-api-docs/reference/Symb/stringtext)
[debugtext](/domino-c-api-docs/reference/Symb/debugtext)
[limitedasciitext](/domino-c-api-docs/reference/Symb/limitedasciitext)
[blocktext](/domino-c-api-docs/reference/Symb/blocktext)
[semtext](/domino-c-api-docs/reference/Symb/semtext)
[donottranslatetext](/domino-c-api-docs/reference/Symb/donottranslatetext)
---
