##### Symbolic Value : Resource Definition
##### apitext - Assign an error code number to a text string.
---
##### #include <globerr.h>
**Description :**
Assigns the given error code to the given text string.  When language 
compiling, the macro actually amounts to nothing more than a comment.  When 
resource compiling a module (RC), the macro is used to map error code numbers 
to a corresponding text string.

Prior to Release 4.5, an alternative form was defined due to a compiler bug in 
MPW C.  The compiler generated an error when a macro evaluated to nothing and 
is followed by another #define.



/* "apitext" designates API-only messages. This could be translated
 (for foreign API programmers) but NEVER shown to a user. */

#define apitext(code,text)

**See Also :**
[errortext](D:/md_files/errortext.md)
[internaltext](D:/md_files/internaltext.md)
[helptext](D:/md_files/helptext.md)
[stringtext](D:/md_files/stringtext.md)
[debugtext](D:/md_files/debugtext.md)
[limitedasciitext](D:/md_files/limitedasciitext.md)
[blocktext](D:/md_files/blocktext.md)
[semtext](D:/md_files/semtext.md)
[donottranslatetext](D:/md_files/donottranslatetext.md)
---
