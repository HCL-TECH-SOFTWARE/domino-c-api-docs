##### Data Type : Composite Data
##### CDBACKGROUNDPROPERTIES - Specifies box background data.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct
 {
 BSIG Header;
 BYTE Repeat;  /*  one of REPEAT_ (see above) */
 BYTE bReserved;
 LENGTH_VALUE lvReservedX;
 LENGTH_VALUE lvReservedY;
 DWORD dwReserved[4];
 } CDBACKGROUNDPROPERTIES;
```

**Description :**

This CD Record gives information pertaining to Background Properties for a box. A CDBACKGROUNDPROPERTIES record may be encapsulated within a CDBEGINRECORD and CDENDRECORD.  
<ul><br>
<br>
Header		Identifies the record as a CDBACKGROUNDPROPERTIES.<br>
Repeat		see REPEAT_xxx <br>
bReserved		Not Used.<br>
lvReservedX	Not Used.<br>
lvReservedY	Not Used.<br>
dwReserved	Not Used.</ul>



**See Also :**
[CDBACKGROUNDPROPERTIES_VERSION1](/domino-c-api-docs/reference/Symb/CDBACKGROUNDPROPERTIES_VERSION1)
[CDBEGINRECORD](/domino-c-api-docs/reference/Data/CDBEGINRECORD)
[CDBOXSIZE](/domino-c-api-docs/reference/Data/CDBOXSIZE)
[CDENDRECORD](/domino-c-api-docs/reference/Data/CDENDRECORD)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
