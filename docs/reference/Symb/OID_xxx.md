##### Symbolic Value : IDs
##### OID_xxx - ORIGINATORID - Sequence
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	OID_SEQNO_MASK	  -  Mask used to extract sequence.

	OID_NO_REPLICATE	  -  Never replicate outward, currently used ONLY for deleted stubs.


**Description :**

The Sequence member of the ORIGINATORID structure is a DWORD used to keep track of the most recent version of the note for replicated data purposes.  Sequence flags are represented in the high order WORD of the Sequence member.  Use these symbols to access the Sequence flags. 


**See Also :**
[ORIGINATORID](/domino-c-api-docs/reference/Data/ORIGINATORID)
---
