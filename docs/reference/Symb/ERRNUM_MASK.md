##### Symbolic Value : Error Handling
##### ERRNUM_MASK - Mask to obtain status code.
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
This mask is used to obtain the 8 bit status value from a STATUS error code.  This mask is useful only with package codes that use the designated 6 bits of the status code.  Newer package codes may use more than 6 bits, leaving fewer than 8 bits for the status value. </ul>



**See Also :**
[ERRNUM](/domino-c-api-docs/reference/Func/ERRNUM)
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
---
