##### Symbolic Value : Miscellaneous
##### OS_TRANSLATE_xxx - Controls the direction in which OSTranslate converts strings.
---
```
#include <osmisc.h>
```

**Symbolic Values :**

	OS_TRANSLATE_NATIVE_TO_LMBCS	  -  Convert the input string from the machine's native character set to LMBCS (optimized for Group 1).

	OS_TRANSLATE_LMBCS_TO_NATIVE	  -  Convert the input string from LMBCS (optimized for Group 1) to the machine's native character set.

	OS_TRANSLATE_LOWER_TO_UPPER	  -  Current international case table.

	OS_TRANSLATE_UPPER_TO_LOWER	  -  Current international case table.

	OS_TRANSLATE_UNACCENT	  -  International unaccenting table.

	OS_TRANSLATE_OSNATIVE_TO_LMBCS	  -  Convert the input string from DOS (code page) to LMBCS (optimized for Group 1).

	OS_TRANSLATE_LMBCS_TO_OSNATIVE	  -  Convert the input string from LMBCS (optimized for Group 1) to DOS.

	OS_TRANSLATE_LMBCS_TO_ASCII	  -  Convert the input string from LMBCS to character text.

	OS_TRANSLATE_LMBCS_TO_UNICODE	  -  Convert the input string from LMBCS to UNICODE.

	OS_TRANSLATE_LMBCS_TO_UTF8	  -  Convert the input string from LMBCS to UTF8.

	OS_TRANSLATE_UNICODE_TO_LMBCS	  -  Convert the input string from UNICODE to LMBCS.

	OS_TRANSLATE_UTF8_TO_LMBCS	  -  Convert the input string from UTF8 to LMBCS.


**Description :**

These flags control the direction in which OSTranslate converts character strings -- either LMBCS to native, or native to LMBCS. <br>
<br>
LMBCS is the Lotus Multi-Byte Character Set.


**See Also :**
[OSTranslate](/domino-c-api-docs/reference/Func/OSTranslate)
---
