##### Data Type : Address Book
##### LOOKUP_INFO - Structure of the data records that are in the buffer returned from NAMELookup.
---
```
#include <lookup.h>
```

**Definition :**

typedef struct {
   WORD         NumMatches;       /* # records which match the name */
/* LOOKUP_MATCH Matches[NumMatches];   ** Array of match buffers... */
} LOOKUP_INFO;

**Description :**

NAMELookup returns a handle to a buffer containing name information. The buffer consists of a header (LOOKUP_HEADER) followed by a series LOOKUP_INFO structures  The order of the LOOKUP_INFO structures correspond to the order of names specified in the Names parameter of the call to NAMELookup.  Each LOOKUP_INFO structure is followed by an array of LOOKUP_MATCH structures.


**See Also :**
[NAMELookup](/domino-c-api-docs/reference/Func/NAMELookup)
[LOOKUP_HEADER](/domino-c-api-docs/reference/Data/LOOKUP_HEADER)
---
