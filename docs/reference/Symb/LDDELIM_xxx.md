##### Symbolic Value : Field
##### LDDELIM_xxx - Defines the separators used to display multiple values in a document field.
---
```
#include <editods.h>
```

**Symbolic Values :**

	LDDELIM_SPACE	  -  When displaying multiple values, separate them with a space.

	LDDELIM_COMMA	  -  When displaying multiple values, separate them with a comma.

	LDDELIM_SEMICOLON	  -  When displaying multiple values, separate them with a semicolon.

	LDDELIM_NEWLINE	  -  When displaying multiple values, separate them with a newline.

	LDDELIM_BLANKLINE	  -  When displaying multiple values, separate them with a blank line.

	LDD_MASK	  -  This may be used to mask out all bits defined for display separators.


**Definition :**
```

```

**Description :**

Used to define  how multiple values will be separated while they are being displayed.  LDELIM_xxx flags define the separators used while entering multiple values in a field, while LDDELIM_xxx flags define the separators that will be used when the multiple values are displayed.


**See Also :**
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
[LDELIM_xxx](/domino-c-api-docs/reference/Symb/LDELIM_xxx)
---
