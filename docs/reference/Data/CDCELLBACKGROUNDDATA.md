##### Data Type : Composite Data
##### CDCELLBACKGROUNDDATA - Specifies Table Background Data.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;
	BYTE  Repeat;
	BYTE  Spare[1];
	DWORD SpareDWORD;
} CDCELLBACKGROUNDDATA;
```

**Description :**

This CD Record gives information pertaining to Background Data for a Table, specifically the 'Cell Image' repeat value.
<ul><br>
<br>
Header		Identifies the record as a CDCELLBACKGROUNDDATA.<br>
Repeat		 see REPEAT_xxx (Table background image settings (Repeat Once, Repeat Vertically, Repeat Horizontally, Center, Size to Fit))<br>
Spare[1]		Not Used.<br>
SpareDWORD	Not Used.</ul>



**See Also :**
[REPEAT_xxx](/domino-c-api-docs/reference/Symb/REPEAT_xxx)
---
