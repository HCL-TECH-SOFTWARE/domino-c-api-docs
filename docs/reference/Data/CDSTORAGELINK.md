##### Data Type : Composite Data
##### CDSTORAGELINK - Structure for externally stored objects.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG Header;
   WORD StorageType; /* Type of object (Object, Note, URL, etc.) */
   WORD LoadType;    /* How to load (deferred, on demand, etc.) */
   WORD Flags;       /* Currently not used */
   WORD DataLength;  /* Length of data following */
   WORD Reserved[6]; /* Currently not used */
/* Storage data follows... */
} CDSTORAGELINK;

**Description :**

This structure stores information for an externally stored object.


**See Also :**
[STORAGE_LINK_LOAD_xxx](/domino-c-api-docs/reference/Symb/STORAGE_LINK_LOAD_xxx)
[STORAGE_LINK_TYPE_xxx](/domino-c-api-docs/reference/Symb/STORAGE_LINK_TYPE_xxx)
---
