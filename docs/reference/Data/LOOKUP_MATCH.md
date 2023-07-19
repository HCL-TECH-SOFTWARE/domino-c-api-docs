##### Data Type : Address Book
##### LOOKUP_MATCH - Structure of each record in the array of match buffers that are in the buffer returned from NAMELookup.
---
```
#include <lookup.h>
```

**Definition :**

typedef struct {
/* WORD        Offset[NumItems];  ** Array of offsets from base of */
                                  /* LOOKUP_MATCH structure to each */
                                  /* item value, in the same order */
                                  /* as the items were provided in */
                                  /* the request. */
   WORD        Length;            /* Length of LOOKUP_MATCH buffer */
                                  /* Acts as Offset[N] array entry */
                                  /* so that to find the length of */
                                  /* any item, you can subtract */
                                  /* Offset[i+1] - Offset[i]. */
/* Item values (datatype and value)... */
} LOOKUP_MATCH;

**Description :**

Structure which is returned for every matching record of a name in a call to NAMELookup.  This structure appears immediately after the LOOKUP_INFO structure.


**See Also :**
[NAMELookup](/domino-c-api-docs/reference/Func/NAMELookup)
[LOOKUP_INFO](/domino-c-api-docs/reference/Data/LOOKUP_INFO)
---
