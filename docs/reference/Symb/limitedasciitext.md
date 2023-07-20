##### Symbolic Value : Resource Definition
##### limitedasciitext - Assign an error code number to a text string.
---
```
#include <globerr.h>
```

**Symbolic Values :**



**Description :**

Assigns the given error code to the given text string.  When language compiling, the macro actually amounts to nothing more than a comment.  When resource compiling a module (RC), the macro is used to map error code numbers to a corresponding text string.
<ul><br>
<br>
/*	&quot;limitedasciitext&quot; designates text which is constrained to a limited<br>
	subset of a platform character set.  One use of this macro is for strings used as<br>
	part of Internet protocols which do not allow for non-platform character text.<br>
	The exact limitations will vary with usage, but will usually be<br>
	restricted to 7-bit character, excluding '\0'.  These strings MAY be<br>
	translated to other languages, but must keep within the limited text<br>
	characters allowed.  For example, translation into French is permitted,<br>
	but no accented characters may be used.<br>
*/<br>
<br>
#define limitedasciitext(code,text)</ul>



**See Also :**
[errortext](/domino-c-api-docs/reference/Symb/errortext)
[helptext](/domino-c-api-docs/reference/Symb/helptext)
[stringtext](/domino-c-api-docs/reference/Symb/stringtext)
[apitext](/domino-c-api-docs/reference/Symb/apitext)
[debugtext](/domino-c-api-docs/reference/Symb/debugtext)
[internaltext](/domino-c-api-docs/reference/Symb/internaltext)
[blocktext](/domino-c-api-docs/reference/Symb/blocktext)
[semtext](/domino-c-api-docs/reference/Symb/semtext)
[donottranslatetext](/domino-c-api-docs/reference/Symb/donottranslatetext)
---
