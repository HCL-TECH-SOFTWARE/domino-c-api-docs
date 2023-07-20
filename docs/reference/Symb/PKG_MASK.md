##### Symbolic Value : Error Handling
##### PKG_MASK - Mask to obtain package code.
---
```
#include <globerr.h>
```

**Symbolic Values :**



**Description :**

The 16-bit value of a STATUS error code consists of the following fields:<br>

<ul>
<ul>1 bit:	Flag bit - status message has been displayed<br>
1 bit:	Flag bit - status message came from a remote machine (i.e., a server)<br>
6 bits:	&quot;Package&quot; code or partial package code<br>
8 bits:	Status value or partial package code plus status value<br>
</ul>
This mask is used to obtain the 6 bit package or subsystem code from a STATUS value.  This mask is useful only with package codes that use the designated 6 bits of the status code.  Newer package codes may use more than 6 bits (leaving fewer than 8 bits for the status value).  </ul>



**See Also :**
[PKG](/domino-c-api-docs/reference/Func/PKG)
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
---
