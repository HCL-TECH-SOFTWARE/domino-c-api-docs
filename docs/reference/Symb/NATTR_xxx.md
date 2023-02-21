##### Symbolic Value : Number
##### NATTR_xxx - NFMT - Attributes.  Specifies attributes for character number strings.
---
```
#include <misc.h>
```
**Description :**

These definitions specify the format for character number strings. Use these 
definitions when you set up the NFMT structure that controls the number format.

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
