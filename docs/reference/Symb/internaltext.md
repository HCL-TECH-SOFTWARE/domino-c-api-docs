##### Symbolic Value : Resource Definition
##### internaltext - Assign an error code number to a text string.
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
/* &quot;internaltext&quot; designates STATUS codes used to indicate a condition<br>
 passed between 2 subsystems, but NEVER displayed to a user. The text<br>
 associated with &quot;internaltext&quot; is NOT EVEN STORED in the executables,<br>
 and thus, never translated or shown to a user. */<br>
<br>
#define internaltext(code,text)<br>
</ul>



**Sample Usage :**
```
#define ERR_QUEUE_NOT_EMPTY PKG_MISC+1
 internaltext(ERR_QUEUE_NOT_EMPTY, "Deleting a non-empty queue")
#define ERR_QUEUE_EMPTY   PKG_MISC+2
 internaltext(ERR_QUEUE_EMPTY,  "No more entries to dequeue")
```

**See Also :**
[errortext](/domino-c-api-docs/reference/Symb/errortext)
[helptext](/domino-c-api-docs/reference/Symb/helptext)
[debugtext](/domino-c-api-docs/reference/Symb/debugtext)
[stringtext](/domino-c-api-docs/reference/Symb/stringtext)
[apitext](/domino-c-api-docs/reference/Symb/apitext)
[blocktext](/domino-c-api-docs/reference/Symb/blocktext)
[semtext](/domino-c-api-docs/reference/Symb/semtext)
[donottranslatetext](/domino-c-api-docs/reference/Symb/donottranslatetext)
[limitedasciitext](/domino-c-api-docs/reference/Symb/limitedasciitext)
---
