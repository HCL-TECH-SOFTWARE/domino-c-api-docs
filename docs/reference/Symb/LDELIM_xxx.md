##### Symbolic Value : Field
##### LDELIM_xxx - Defines the input separators used with multiple values in a document field.
---
```
#include <editods.h>
```

**Symbolic Values :**

	LDELIM_SPACE	  -  When inputting multiple values, separate them with a space.

	LDELIM_COMMA	  -  When inputting multiple values, separate them with a comma.

	LDELIM_SEMICOLON	  -  When inputting multiple values, separate them with a semicolon.

	LDELIM_NEWLINE	  -  When inputting multiple values, separate them with a newline.

	LDELIM_BLANKLINE	  -  When inputting multiple values, separate them with a blank line.

	LD_MASK	  -  This may be used to mask out all bits defined for input separators.


**Description :**

Used to define  how multiple values will be separated while they are being input.  LDELIM_xxx flags define the separators used while entering multiple values in a field, while LDDELIM_xxx flags define the separators that will be used when the multiple values are displayed.


**See Also :**
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
[LDDELIM_xxx](/domino-c-api-docs/reference/Symb/LDDELIM_xxx)
---
