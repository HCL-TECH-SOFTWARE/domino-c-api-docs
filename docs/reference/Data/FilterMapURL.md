##### Data Type : DSAPI
##### FilterMapURL - URL map
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct {
	const char*  url;   /* Input. The input URL */
	char*   pathBuffer;  /* Input. The resulting mapping is contained in 
the supplied buffer */
	unsigned int bufferSize;  /* Size of the buffer supplied */
	unsigned int mapType;  /* Mapping type. */
} FilterMapURL;

**Description :**

Input
<ul>
<ul><br>
url<b><i>-</i></b> Input parameter. It is a pointer to a string whose value is the <br>
current url being processed.<br>
<br>
bufferSize - Input parameter. This is the size of the supplied buffer in which to store the new url.<br>
<br>
Output <br>
<br>
pathBuffer -<b><i> </i></b>Ouput parameter. It is a pointer to a supplied buffer where the the new url is to be stored.<br>
<br>
mapType<b><i> - </i></b>Output parameter. If applicable, see FilterURLMapTypes for more information.</ul>
</ul>



**See Also :**
---
