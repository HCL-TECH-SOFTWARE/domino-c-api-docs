##### Data Type : Composite Data
##### CDOLEEND - Specifies the end of an OLE Object.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header; /* Signature and length of this record */ 
   DWORD Flags; /* Currently unused, but reserve some flags */
}CDOLEEND;
```

**Description :**

This structure specifies the end of an OLE Object in a rich text field.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.


**See Also :**
[CDOLEBEGIN](/domino-c-api-docs/reference/Data/CDOLEBEGIN)
---
