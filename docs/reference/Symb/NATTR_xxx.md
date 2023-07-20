##### Symbolic Value : Number
##### NATTR_xxx - NFMT - Attributes.  Specifies attributes for character number strings.
---
```
#include <misc.h>
```

**Symbolic Values :**

	NATTR_PUNCTUATED	  -  The number will be punctuated by the appropriate separator character.

	NATTR_PARENS	  -  Negative numbers will be displayed in parentheses, rather than being preceded by a minus sign.

	NATTR_PERCENT	  -  The number entered will be interpreted as a percentage, and will be converted to its decimal equivalent by moving the decimal point two places to the left.

	NATTR_VARYING	  -  Numbers can have a varying number of decimal places (applies to Decimal & Percent only).


**Description :**

These definitions specify the format for character number strings. Use these definitions when you set up the NFMT structure that controls the number format.


**Sample Usage :**
```

/*
 *  Set up Number format
 */  

NFMT NumberFormat;  

NumberFormat.Digits     = 6;
NumberFormat.Format     = NFMT_GENERAL;
NumberFormat.Attributes = NATTR_PUNCTUATED;
NumberFormat.Unused     = 0;



```

**See Also :**
[NFMT](/domino-c-api-docs/reference/Data/NFMT)
---
