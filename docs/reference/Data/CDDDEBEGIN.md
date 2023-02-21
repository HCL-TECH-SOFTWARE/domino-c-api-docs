##### Data Type : Composite Data
##### CDDDEBEGIN - Specifies the start of a DDE link.
---
```
#include <editods.h>
```
**Description :**

A CD record of this type specifies the start of a DDE link.

Note that CDDDEBEGIN records reside in items of type TYPE_COMPOSITE. Therefore, 
API programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on structures of this type when accessing these 
records in an item in a note.

**See Also :**
[CDDDEEND](/domino-c-api-docs/reference/Data/CDDDEEND)
---
