##### Data Type : Number
##### NFMT - Formats for character text number string conversions.
---
```
#include <misc.h>
```
**Description :**

This structure holds the format for character text number strings. You set up 
this structure based on the number format you want to use. Definitions for the 
various fields of this structure are found in NFMT_xxx and NATTR_xxx.

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
[NATTR_xxx](/reference/Symb/NATTR_xxx)
[NFMT_xxx](/reference/Symb/NFMT_xxx)
---
