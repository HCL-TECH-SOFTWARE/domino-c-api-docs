##### Symbolic Value : Error Handling
##### ERR_MASK - Mask used to remove flag bits.
---
```
#include <globerr.h>
```
**Description :**

The 16-bit value of a STATUS error code consists of the following fields:

1 bit: Flag bit - status message has been displayed
1 bit: Flag bit - status message came from a remote machine (i.e., a server)
6 bits: "Package" code or partial package code
8 bits: Status value or partial package code plus status value

This mask is used to remove the flag bits, leaving the package code and error 
code.

**See Also :**
[ERR](/domino-c-api-docs/reference/Func/ERR)
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
---
