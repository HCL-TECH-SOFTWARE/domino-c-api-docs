##### Function : Rich Text
##### GETDATABORDERTYPE - Return the data border type value stored in a CDDATAFLAGS structure.
---
```
#include <editods.h>
DWORD GETDATABORDERTYPE(

	DWORD  a);
```
**Description :**

This macro returns the data border type value that is stored in the CDDATAFLAGS 
structure and is defined as follows:

#define GETDATABORDERTYPE(a) (((DWORD)((a) & BARREC_DATA_BORDER_MASK )) + 
BAR_DATA_BORDER_OFFSET)

See the BARREC_DATA_BORDER_xxx symbolic for possible return values.

**Parameters :**
Input :
a  -  A Flags member of the CDDATAFLAGS structure.  This macro returns the border type that is stored in this DWORD.

Output :
(routine)  -  The border type that is set in the Flags member of a CDDATAFLAGS structure.  See the BARREC_DATA_BORDER_xxx symbolic values.



**See Also :**
[BARREC_DATA_BORDER_xxx](/domino-c-api-docs/reference/Symb/BARREC_DATA_BORDER_xxx)
[CDDATAFLAGS](/domino-c-api-docs/reference/Data/CDDATAFLAGS)
---
