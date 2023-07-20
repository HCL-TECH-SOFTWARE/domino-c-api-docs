##### Data Type : Composite Data
##### CDTARGET - Defines a TARGET area for a resource link hotspot.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;
   WORD  TargetLength;
   WORD  Flags;
   DWORD Reserved;
 } CDTARGET;
```

**Description :**

WSIG	Header		Signature and length of record
<ul><br>
WORD	TargetLength	length of the data following this record <br>
WORD	Flags	see FLAG_TARGET_xxx<br>
DWORD	Reserved<br>
<br>
The name of the target frame follows.<br>
<br>
The CDTARGET structure specifies the target (ie:  the frame) where a resource link hotspot is to be displayed.<br>
It is followed by variable length data whose length is specified in the TargetLength member.  This variable length data specifies the target frame.  The format of the variable length data is specified by the Flags member of the CDTARGET structure.  If no flags are specified, then the data following the CDTARGET record is a character string containing the name of the target frame.</ul>



**See Also :**
[FLAG_TARGET_xxx](/domino-c-api-docs/reference/Symb/FLAG_TARGET_xxx)
---
