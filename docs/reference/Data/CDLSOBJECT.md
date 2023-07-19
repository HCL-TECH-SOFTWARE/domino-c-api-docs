##### Data Type : Composite Data
##### CDLSOBJECT - Lotus Script object code
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
	 WSIG Header;
	 DWORD   CodeSize; /* Total code size for multiple code segments, for 
R6 >64k */
   BYTE Reserved[4];
	 /* Lotus Script object code follows */
} CDLSOBJECT;

**Description :**

The CD record contains Lotus Script object code.  The fields in this record are:
<ul><br>

<ul>Header		Identifies this record as a CDLSOBJECT structure.<br>
CodeSize	Total code size for multiple code segments.<br>
Reserved	Reserved;  must be 0.</ul>
</ul>



**See Also :**
[CDHOTSPOTBEGIN](/domino-c-api-docs/reference/Data/CDHOTSPOTBEGIN)
[CDLSOBJECT_R6](/domino-c-api-docs/reference/Data/CDLSOBJECT_R6)
---
