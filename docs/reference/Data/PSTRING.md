##### Data Type : Dynamic Array
##### PSTRING - Packed string descriptor.
---
```
#include <darray.h>
```

**Definition :**

typedef struct {
    WORD StringSize;  /* String size */
    WORD StringType;  /* String type (info only) */
    char far *String; /* String pointer or offset */
} PSTRING;

**Description :**

Structure defining a packed string for a dynamic array.  This structure is incorporated into a structure to be stored as an element in a dynamic array.  Any PSTRING structures <u>must</u> be the <u>last</u> members of the element structure.
<ul><br>
<br>
The member StringType is optional, and may be used by applications to store any 16-bit value.  The members StringSize and String are required, and must be set correctly before the element is stored in the dynamic array.<br>
<br>
Before an element is stored in a dynamic array, the String member must be a pointer to the packed string data.  This data need not be contiguous with the element record.  Once the element is stored in the dynamic array, the String member in the element record stored in the dynamic array becomes an offset into the packed string store for that dynamic array.  (The original member structure is not modified.)</ul>



**See Also :**
[DARRAY](/domino-c-api-docs/reference/Data/DARRAY)
[OSDArrayAddElement](/domino-c-api-docs/reference/Func/OSDArrayAddElement)
[OSDArray](/domino-c-api-docs/reference/Func/OSDArray)
[OSDArrayRemoveElement](/domino-c-api-docs/reference/Func/OSDArrayRemoveElement)
---
