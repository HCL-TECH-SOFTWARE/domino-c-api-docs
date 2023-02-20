##### Data Type : Composite Data
##### CDTABLELABEL - Specifies Table Label information.
---
```
#include <editods.h>
```
**Description :**

This CD Record further defines information for a table.  Specifically the tab 
and row labels.

WSIG Header  Signature and length of this record.
char Label[128] Label value, either tab or row label.
WORD Reserved[3]
WORD Flags  see CDTABLELABEL_xxx

**See Also :**
[CDTABLELABEL_xxx](/reference/Symb/CDTABLELABEL_xxx)
---
