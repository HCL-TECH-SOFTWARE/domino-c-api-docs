##### Data Type : Character Manipulation
##### NLS_INFO - The data structure that defines the attributes of a character set.
---
```
#include <nls.h>
```

**Definition :**

typedef void NLS_INFO;

**Description :**

An NLS_INFO struct defines the attributes of a character set.  It contains a number of flags and pointers to various translation tables.  Most of the National Language Services (NLS) functions take a pointer to an NLS_INFO struct as one of their arguments.  You should initialize the NLS_INFO struct by calling the function OSGetLMBCSCLS() before calling one of the NLS functions.
<ul><br>
<br>
<b>Note:</b> This data structure should be treated as READ-ONLY -- modifying the data structure could have undesired consequences.</ul>



**See Also :**
[NLS_PINFO](/domino-c-api-docs/reference/Data/NLS_PINFO)
---
