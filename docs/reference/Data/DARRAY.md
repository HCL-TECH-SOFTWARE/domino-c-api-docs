##### Data Type : Dynamic Array
##### DARRAY - Dynamic array header structure.
---
```
#include <darray.h>
```
**Description :**

Dynamic arrays are used internally by Domino and Notes to manage collections of 
information in memory that require frequent insertions and deletions.  A 
dynamic array has three components:

1)  The DARRAY structure, which contains control information.
2)  An array of element structures of fixed size.
3)  Storage for packed strings;  strings can have any length, and are described 
by PSTRING structures contained in the element structures.

The element structures can be any size, but all element structures in one 
DARRAY must be the same size.  Any PSTRING structures must be the last members 
of the element structures.

The size of the entire dynamic array cannot exceed MAXONESEGSIZE in size.

**See Also :**
[MAXONESEGSIZE](/reference/Symb/MAXONESEGSIZE)
[PSTRING](/reference/Data/PSTRING)
[OSDArray](/reference/Func/OSDArray)
[OSDArrayAddElement](/reference/Func/OSDArrayAddElement)
[OSDArrayAlloc](/reference/Func/OSDArrayAlloc)
[OSDArrayRemoveElement](/reference/Func/OSDArrayRemoveElement)
---
