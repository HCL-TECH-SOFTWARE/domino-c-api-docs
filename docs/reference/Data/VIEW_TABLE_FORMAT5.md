##### Data Type : Views
##### VIEW_TABLE_FORMAT5 - Contains additional view format information for Domino R6.
---
```
#include <viewfmt.h>
```

**Definition :**
```
typedef struct
{
   WORD   Length;       /* Length of this structure */
   DWORD  Flags;        /* Reserved for future use */
   WORD   RepeatType;   /* see viewprop.h - way to repeat image */
} VIEW_TABLE_FORMAT5;
```

**Description :**




**See Also :**
---
