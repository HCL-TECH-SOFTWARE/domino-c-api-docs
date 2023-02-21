##### Data Type : Composite Data
##### CDTIMERINFO - Specifies time interval information
---
```
#include <editods.h>
```
**Description :**

This CD record provides the time interval information for tables created where 
a different row is displayed within the time interval specified.  This 
structure is stored just before the CDTABLEEND structure.

BSIG Header  CD Signature and length
DWORD Interval  The time interval  in milliseconds.

**See Also :**
[CDTABLEVIEWER_xxx](/domino-c-api-docs/reference/Symb/CDTABLEVIEWER_xxx)
[CDTABLEEND](/domino-c-api-docs/reference/Data/CDTABLEEND)
---
