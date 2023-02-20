##### Data Type : Dynamic Array
##### PSTRING - Packed string descriptor.
---
```
#include <darray.h>
```
**Description :**

Structure defining a packed string for a dynamic array.  This structure is 
incorporated into a structure to be stored as an element in a dynamic array.  
Any PSTRING structures must be the last members of the element structure.

The member StringType is optional, and may be used by applications to store any 
16-bit value.  The members StringSize and String are required, and must be set 
correctly before the element is stored in the dynamic array.

Before an element is stored in a dynamic array, the String member must be a 
pointer to the packed string data.  This data need not be contiguous with the 
element record.  Once the element is stored in the dynamic array, the String 
member in the element record stored in the dynamic array becomes an offset into 
the packed string store for that dynamic array.  (The original member structure 
is not modified.)

**See Also :**
[DARRAY](/reference/Data/DARRAY)
[OSDArrayAddElement](/reference/Func/OSDArrayAddElement)
[OSDArray](/reference/Func/OSDArray)
[OSDArrayRemoveElement](/reference/Func/OSDArrayRemoveElement)
---
