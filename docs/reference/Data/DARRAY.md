##### Data Type : Dynamic Array
##### DARRAY - Dynamic array header structure.
---
```
#include <darray.h>
```

**Definition :**

typedef struct {
    WORD ObjectSize;             /* Total array object size */
    WORD ElementsUsed;           /* Elements in use */
    WORD ElementsFree;           /* Free elements */
    WORD ElementsFreeMax;        /* Maximum free elements */
    WORD ElementsFreeExtra;      /* Extra free elements to maintain */
    WORD ElementSize;            /* Element size in bytes */
    WORD ElementStrings;         /* Number packed string descriptors
                                    in each element */
    WORD StringStorageOffset;    /* Offset to packed string storage */
    WORD StringStorageUsed;      /* In use bytes of string storage */
    WORD StringStorageFree;      /* Free bytes of string storage */
    WORD StringStorageFreeMax;   /* Maximum free storage */
    WORD StringStorageFreeExtra; /* Extra free storage to maintain */

/*  First array element follows here.  First byte of packed string
/*  storage follows last allocated array element. */

} DARRAY;

**Description :**

Dynamic arrays are used internally by Domino and Notes to manage collections of information in memory that require frequent insertions and deletions.  A dynamic array has three components:
<ul><br>

<ul>1)  The DARRAY structure, which contains control information.<br>
2)  An array of element structures of fixed size.<br>
3)  Storage for packed strings;  strings can have any length, and are described by PSTRING structures contained in the element structures.</ul>
<br>
The element structures can be any size, but all element structures in one DARRAY must be the same size.  Any PSTRING structures must be the last members of the element structures.<br>
<br>
The size of the entire dynamic array cannot exceed MAXONESEGSIZE in size.</ul>



**See Also :**
[MAXONESEGSIZE](/domino-c-api-docs/reference/Symb/MAXONESEGSIZE)
[PSTRING](/domino-c-api-docs/reference/Data/PSTRING)
[OSDArray](/domino-c-api-docs/reference/Func/OSDArray)
[OSDArrayAddElement](/domino-c-api-docs/reference/Func/OSDArrayAddElement)
[OSDArrayAlloc](/domino-c-api-docs/reference/Func/OSDArrayAlloc)
[OSDArrayRemoveElement](/domino-c-api-docs/reference/Func/OSDArrayRemoveElement)
---
