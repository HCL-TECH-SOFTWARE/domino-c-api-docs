##### Data Type : Composite Data
##### CDBLOBPART - Structure which defines a 'Binary Large Object'
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;   /* Signature and length of this record) */
   WORD OwnerSig; /* Sig of the owner of this data */
   WORD Length;   /* Length of the data that follows */
   WORD BlobMax;  /* Block size used by the writer of the blob */
   BYTE Reserved[8];
} CDBLOBPART;
```

**Description :**

This CD record is used in conjunction with CD record CDEVENT.  If a CDEVENT record has an ActionType of ACTION_TYPE_JAVASCRIPT then CDBLOBPART contains the JavaScript code.  There may be more then one CDBLOBPART record for each CDEVENT.  Therefore it may be necessary to loop thorough all of the CDBLOBPART records to read in the complete JavaScript code.


**See Also :**
[CDEVENT](/domino-c-api-docs/reference/Data/CDEVENT)
---
