##### Data Type : HTML
##### USV - URL Specal Values
---
```
#include <urltypes.h>
```

**Definition :**

typedef enum _USV
{
    USV_About               = 0,
    USV_Help                = 1,
    USV_Icon                = 2,
    USV_DefaultView         = 3,
    USV_DefaultForm         = 4,
    USV_DefaultNav          = 5,
    USV_SearchForm          = 6,
    USV_DefaultOutline      = 7,
    USV_First               = 8,
    USV_FileField           = 9,
/* SDK END */
                        /* <= add new types above here 
                                do not reuse numbers, do not rely on 
"USV_NumberOfTypes"
                                being the same on each side of the API */
/* SDK BEGIN */
    USV_NumberOfValues          /* must be the last one */
} USV;

**Description :**

<tt>values that stand for the &quot;special name&quot; URL components.</tt>


**See Also :**
---
