##### Symbolic Value : Error Handling
##### ERR_MASK - Mask used to remove flag bits.
---
```
#include <globerr.h>
```

**Symbolic Values :**



**Description :**

The 16-bit value of a STATUS error code consists of the following fields:
<ul><br>

<ul>1 bit:	Flag bit - status message has been displayed<br>
1 bit:	Flag bit - status message came from a remote machine (i.e., a server)<br>
6 bits:	&quot;Package&quot; code or partial package code<br>
8 bits:	Status value or partial package code plus status value<br>
</ul>
This mask is used to remove the flag bits, leaving the package code and error code.</ul>



**See Also :**
[ERR](/domino-c-api-docs/reference/Func/ERR)
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
---
