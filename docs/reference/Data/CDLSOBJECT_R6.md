##### Data Type : Composite Data
##### CDLSOBJECT_R6 - LotusScript object code for Notes/Domino 6
---
```
#include <editods.h>
```

**Definition :**

typedef struct
 {
 WSIG Header;
#define CDLSOBJECT_R6_TYPE  01  /* signals multiple code segments for R6 >64k */
 BYTE    Flags;
 BYTE Reserved[7]; 
 } CDLSOBJECT_R6;

**Description :**

This CD record contains Lotus Script object code for Notes/Domino 6.  The fields in this record are:
<ul><br>

<ul>Header		Signature and Length of this CD record.<br>
Flags		Lotus Script Object Flags for Notes/Domino 6. <br>
Reserved	Reserved for future use.</ul>
</ul>



**See Also :**
[CDLSOBJECT](/domino-c-api-docs/reference/Data/CDLSOBJECT)
[CDLSOBJECT_R6_TYPE](/domino-c-api-docs/reference/Symb/CDLSOBJECT_R6_TYPE)
---
