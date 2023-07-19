##### Data Type : HTML
##### URT - URL Reference Type
---
```
#include <urltypes.h>
```

**Definition :**

typedef enum _URT       /* Reference types */
{
    URT_None                = 0,
    URT_Name                = 1,
    URT_Unid                = 2,
    URT_NoteId              = 3,
    URT_Special             = 4,    /* special name */
    URT_RepId               = 5,
/* SDK END */
                        /* <= add new types above here 
                                do not reuse numbers, do not rely on 
"URT_NumberOfTypes"
                                being the same on each side of the API */
/* SDK BEGIN */
    URT_NumberOfTypes           /* must be the last one */
} URT;


**Description :**

<tt>This enumerates ways a Notes Object can be references in a URL path.</tt>


**Sample Usage :**
```
see sample html/convattach
```

**See Also :**
[HTMLAPI_URLTargetComponent](/domino-c-api-docs/reference/Data/HTMLAPI_URLTargetComponent)
---
