##### Symbolic Value : Number
##### NFMT_xxx - NFMT - Format.  Specifies the format for character number strings.
---
```
#include <misc.h>
```

**Symbolic Values :**

	NFMT_GENERAL	  -  Only the significant digits in a number will be displayed; leading zeroes and trailing zeroes will be stripped.

	NFMT_FIXED	  -  The number displayed will contain to the right of the decimal point the number of digits specified in the NFMT->Digits structure member. The number will be either truncated or padded with zeroes, as appropriate.

	NFMT_SCIENTIFIC	  -  The number will be displayed in scientific notation.

	NFMT_CURRENCY	  -  The appropriate currency symbol will be displayed with the number.


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
