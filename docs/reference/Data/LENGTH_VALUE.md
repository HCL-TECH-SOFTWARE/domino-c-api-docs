##### Data Type : Rich Text
##### LENGTH_VALUE - Structure used to store a length to disk. 
---
```
#include <editods.h>
```

**Definition :**

typedef struct
 {
 WORD    Flags;
 ALIGNED_NUMBER Length;
 BYTE    Units;
 BYTE    Reserved; /* reserved for future use */
 } LENGTH_VALUE;


**Description :**

This record contains information for storing a length to disk.  The fields in this record are:
<ul><br>

<ul>Flags		See CDLENGTH_FLAGS_xxx. <b> </b><br>
Length		Length of the record.<br>
Units		See CDLENGTH_UNITS_xxx. <b> </b><br>
Reserved	Reserved for future use.</ul>
</ul>



**See Also :**
[CDBACKGROUNDPROPERTIES](/domino-c-api-docs/reference/Data/CDBACKGROUNDPROPERTIES)
[CDBOXSIZE](/domino-c-api-docs/reference/Data/CDBOXSIZE)
[CDLENGTH_FLAGS_xxx](/domino-c-api-docs/reference/Symb/CDLENGTH_FLAGS_xxx)
[CDLENGTH_UNITS_xxx](/domino-c-api-docs/reference/Symb/CDLENGTH_UNITS_xxx)
[CDPOSITIONING](/domino-c-api-docs/reference/Data/CDPOSITIONING)
---
