##### Data Type : Rich Text
##### CDHTMLFORMULA - Formula for attributes or alternate HTML text.
---
```
#include <editods.h>
```
**Description :**

A CDHTMLFORMULA record contains a formula used to generate either an attribute 
or alternate HTML text for a Java applet.  The fields in this structure are:

Header  Identifies this as a CDHTMLFORMULA record.
dwFlags Flags for this record;  see CDHTMLFORMULA_FLAG_xxx.
cbLevel 
cbReserved Reserved;  must be 0.
Reserved Reserved;  must be 0.

This record is followed by the actual formula.

**See Also :**
[CDHTMLFORMULA_FLAG_xxx](/reference/Symb/CDHTMLFORMULA_FLAG_xxx)
---
