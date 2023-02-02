##### Symbolic Value : Resource Definition
##### donottranslatetext - Assign an error code number to a text string.
---
##### #include <globerr.h>
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
[errortext](D:/md_files/errortext.md)
[helptext](D:/md_files/helptext.md)
[stringtext](D:/md_files/stringtext.md)
[apitext](D:/md_files/apitext.md)
[debugtext](D:/md_files/debugtext.md)
[internaltext](D:/md_files/internaltext.md)
[blocktext](D:/md_files/blocktext.md)
[semtext](D:/md_files/semtext.md)
[limitedasciitext](D:/md_files/limitedasciitext.md)
---
