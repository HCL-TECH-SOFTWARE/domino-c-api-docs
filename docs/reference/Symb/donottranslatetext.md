##### Symbolic Value : Resource Definition
##### donottranslatetext - Assign an error code number to a text string.
---
```
#include <globerr.h>
```
**Description :**

Assigns the given error code to the given text string.  When language 
compiling, the macro actually amounts to nothing more than a comment.  When 
resource compiling a module (RC), the macro is used to map error code numbers 
to a corresponding text string.

/* "donottranslatetext" designates text which must not be translated.
 This text may be included in a resource file in order to facilitate
 configuration changes, such as a string which controls program behavior.
 Or it may be included in order to clearly indicate that the developer
 intends for the text to remain untranslated.
*/

#define donottranslatetext(code,text)

**See Also :**
[errortext](/reference/Symb/errortext)
[helptext](/reference/Symb/helptext)
[stringtext](/reference/Symb/stringtext)
[apitext](/reference/Symb/apitext)
[debugtext](/reference/Symb/debugtext)
[internaltext](/reference/Symb/internaltext)
[blocktext](/reference/Symb/blocktext)
[semtext](/reference/Symb/semtext)
[limitedasciitext](/reference/Symb/limitedasciitext)
---
