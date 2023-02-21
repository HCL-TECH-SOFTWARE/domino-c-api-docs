##### Symbolic Value : Error Handling
##### STS_xxx - Error code status flags.
---
```
#include <globerr.h>
```
**Description :**

The 16-bit value of a STATUS error code consists of two bit flags, a subsystem 
code, and an error code specific to the subsystem.The top two bits of the error 
code are reserved for the bit flags and indicate an error code status ; four 
values can be encoded of which two are currently used.

**See Also :**
[ERR](/domino-c-api-docs/reference/Func/ERR)
[ERR_MASK](/domino-c-api-docs/reference/Symb/ERR_MASK)
---
