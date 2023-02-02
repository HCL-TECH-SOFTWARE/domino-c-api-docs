##### Symbolic Value : Resource Definition
##### limitedasciitext - Assign an error code number to a text string.
---
##### #include <globerr.h>
**Description :**
Assigns the given error code to the given text string.  When language 
compiling, the macro actually amounts to nothing more than a comment.  When 
resource compiling a module (RC), the macro is used to map error code numbers 
to a corresponding text string.

/* "limitedasciitext" designates text which is constrained to a limited
 subset of a platform character set.  One use of this macro is for strings used 
as
 part of Internet protocols which do not allow for non-platform character text.
 The exact limitations will vary with usage, but will usually be
 restricted to 7-bit character, excluding '\0'.  These strings MAY be
 translated to other languages, but must keep within the limited text
 characters allowed.  For example, translation into French is permitted,
 but no accented characters may be used.
*/

#define limitedasciitext(code,text)
**See Also :**
[errortext](D:/md_files/errortext.md)
[helptext](D:/md_files/helptext.md)
[stringtext](D:/md_files/stringtext.md)
[apitext](D:/md_files/apitext.md)
[debugtext](D:/md_files/debugtext.md)
[internaltext](D:/md_files/internaltext.md)
[blocktext](D:/md_files/blocktext.md)
[semtext](D:/md_files/semtext.md)
[donottranslatetext](D:/md_files/donottranslatetext.md)
---
