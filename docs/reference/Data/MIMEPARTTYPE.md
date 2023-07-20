##### Data Type : MIME
##### MIMEPARTTYPE - MIME_PART - cPartType
---
```
#include <mimeods.h>
```

**Definition :**
```
typedef enum tagMIMEPartType {
 MIME_PART_PROLOG  = 1,
 MIME_PART_BODY  = 2,
 MIME_PART_EPILOG  = 3,
 MIME_PART_RETRIEVE_INFO = 4,
 MIME_PART_MESSAGE  = 5
} MIMEPARTTYPE;
```

**Description :**

The mime part type cPartType within the MIME_PART structure.
<ul><br>
<br>
MIME_PART_PROLOG		- Mime part type is a prolog.<br>
MIME_PART_BODY		- Mime part type is a body.<br>
MIME_PART_EPILOG		- Mime part type is a epilog.<br>
MIME_PART_RETRIEVE_INFO	- Mime part type is retrieve information.<br>
MIME_PART_MESSAGE		- Mime part type is a message.</ul>



**See Also :**
[MIME_PART](/domino-c-api-docs/reference/Data/MIME_PART)
---
