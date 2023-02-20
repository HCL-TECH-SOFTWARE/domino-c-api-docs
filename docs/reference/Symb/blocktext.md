##### Symbolic Value : Resource Definition
##### blocktext - Assign an error code number to a text string.
---
```
#include <globerr.h>
```
**Description :**

Assigns the given error code to the given text string.  When language 
compiling, the macro actually amounts to nothing more than a comment.  When 
resource compiling a module (RC), the macro is used to map error code numbers 
to a corresponding text string.

Prior to Release 4.5, an alternative form was defined due to a compiler bug in 
MPW C.  The compiler generated an error when a macro evaluated to nothing and 
is followed by another #define.


/* "blocktext" designates DEBUG-only descriptions of internal storage
 allocation types. This is not to be translated and never shown to a user. */

#define blocktext(code,text)


**See Also :**
[errortext](/reference/Symb/errortext)
[helptext](/reference/Symb/helptext)
[stringtext](/reference/Symb/stringtext)
[apitext](/reference/Symb/apitext)
[debugtext](/reference/Symb/debugtext)
[internaltext](/reference/Symb/internaltext)
[semtext](/reference/Symb/semtext)
[donottranslatetext](/reference/Symb/donottranslatetext)
[limitedasciitext](/reference/Symb/limitedasciitext)
---
