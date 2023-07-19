##### Data Type : DSAPI
##### FilterRawWrite - Write content
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct {
	char*   content;
	unsigned int contentLen;
	unsigned int reserved;
} FilterRawWrite;

**Description :**

content - Input/Output parameter. It is a pointer to a buffer that contains the data to send to the client. The filter can change the data in place (using the same buffer) or allocate a new buffer and fill it.
<ul>
<ul><br>
contentLen Input/Output parameter. It is the number of valid bytes in the supplied buffer on input, and/or the number of valid bytes in the buffer on output.<br>
<br>
reserved<b> -</b> reserved for future use.</ul>
</ul>



**See Also :**
---
