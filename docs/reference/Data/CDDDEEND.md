##### Data Type : Composite Data
##### CDDDEEND - Specifies the end of a DDE link.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG  Header; /* Signature and length of this record */ 
   DWORD Flags;  /* Currently unused, but reserve some flags */
}CDDDEEND;

**Description :**

This structure specifies the end of a DDE link.<br>
<br>
Note that CDDDEEND records reside in items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CDDEEEND structures when accessing these records in an item in a note.


**See Also :**
[CDDDEBEGIN](/domino-c-api-docs/reference/Data/CDDDEBEGIN)
---
