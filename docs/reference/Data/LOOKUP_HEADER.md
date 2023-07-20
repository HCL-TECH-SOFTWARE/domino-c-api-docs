##### Data Type : Address Book
##### LOOKUP_HEADER - Structure of the header of the buffer returned from NAMELookup.
---
```
#include <lookup.h>
```

**Definition :**
```
typedef struct {
   WORD        Length;     /* Length of entire buffer */
   WORD        NumItems;   /* # items returned with each match */
/* LOOKUP_INFO NameInfo[NumNames]; ** Array of info for each name
                                      looked up */
} LOOKUP_HEADER;
```

**Description :**

NAMELookup returns a handle to a buffer containing name information. The buffer consists of this header followed by a series of data records.


**See Also :**
[NAMELookup](/domino-c-api-docs/reference/Func/NAMELookup)
[LOOKUP_INFO](/domino-c-api-docs/reference/Data/LOOKUP_INFO)
---
