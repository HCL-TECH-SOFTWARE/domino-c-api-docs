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
[errortext](/domino-c-api-docs/reference/Symb/errortext)
[helptext](/domino-c-api-docs/reference/Symb/helptext)
[stringtext](/domino-c-api-docs/reference/Symb/stringtext)
[apitext](/domino-c-api-docs/reference/Symb/apitext)
[debugtext](/domino-c-api-docs/reference/Symb/debugtext)
[internaltext](/domino-c-api-docs/reference/Symb/internaltext)
[blocktext](/domino-c-api-docs/reference/Symb/blocktext)
[semtext](/domino-c-api-docs/reference/Symb/semtext)
[limitedasciitext](/domino-c-api-docs/reference/Symb/limitedasciitext)
---
