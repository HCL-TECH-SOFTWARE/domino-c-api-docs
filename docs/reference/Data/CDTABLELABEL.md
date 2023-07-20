##### Data Type : Composite Data
##### CDTABLELABEL - Specifies Table Label information.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;
   char Label[128];
   WORD Reserved[3];
   WORD Flags;
} CDTABLELABEL; 
```

**Description :**

This CD Record further defines information for a table.  Specifically the tab and row labels.
<ul><br>
<br>
WSIG	Header		Signature and length of this record.<br>
char	Label[128]	Label value, either tab or row label.<br>
WORD	Reserved[3]<br>
WORD	Flags		see CDTABLELABEL_xxx</ul>



**See Also :**
[CDTABLELABEL_xxx](/domino-c-api-docs/reference/Symb/CDTABLELABEL_xxx)
---
