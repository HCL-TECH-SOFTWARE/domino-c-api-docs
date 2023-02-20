##### Symbolic Value : Resource Definition
##### helptext - Assign an error code number to a text string.
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


/* "helptext" designates the "Menu Help" messages displayed on the top
 line of the screen when you drag across a menu item. There is usually
 also further online help associated with each of these menu items. */

#define helptext(code,text)


**See Also :**
[errortext](/reference/Symb/errortext)
[stringtext](/reference/Symb/stringtext)
[apitext](/reference/Symb/apitext)
[debugtext](/reference/Symb/debugtext)
[internaltext](/reference/Symb/internaltext)
[blocktext](/reference/Symb/blocktext)
[semtext](/reference/Symb/semtext)
[limitedasciitext](/reference/Symb/limitedasciitext)
[donottranslatetext](/reference/Symb/donottranslatetext)
---
