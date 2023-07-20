##### Data Type : Composite Data
##### CDTIMERINFO - Specifies time interval information
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   BSIG  Header;
   DWORD Interval;
   WORD  Reserved[4];
} CDTIMERINFO; 
```

**Description :**

This CD record provides the time interval information for tables created where a different row is displayed within the time interval specified.  This structure is stored just before the CDTABLEEND structure.
<ul><br>
<br>
BSIG	Header		CD Signature and length<br>
DWORD	Interval		The time interval  in milliseconds.</ul>



**See Also :**
[CDTABLEVIEWER_xxx](/domino-c-api-docs/reference/Symb/CDTABLEVIEWER_xxx)
[CDTABLEEND](/domino-c-api-docs/reference/Data/CDTABLEEND)
---
