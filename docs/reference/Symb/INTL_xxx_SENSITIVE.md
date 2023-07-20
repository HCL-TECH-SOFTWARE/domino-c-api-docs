##### Symbolic Value : International Character Manipulation
##### INTL_xxx_SENSITIVE - International collation options.
---
```
#include <misc.h>
```

**Symbolic Values :**

	INTL_ACCENT_SENSITIVE	  -  Collation is accent-sensitive. If set, accented and unaccented characters are treated as different characters. If not set, they are treated as the same character. Accent removal is performed according to rules in the current collation table.

	INTL_CASE_SENSITIVE	  -  Collation is case-sensitive. If set, upper-case and lower-case chacters are treated as different characters. If not set, they are treated as the same character. Upper-case and lower-case conversion is performed according to rules in the current collation table.


**Description :**

These options are used with international character string functions to specify collation options.


**See Also :**
[IntlTextCompare](/domino-c-api-docs/reference/Func/IntlTextCompare)
---
