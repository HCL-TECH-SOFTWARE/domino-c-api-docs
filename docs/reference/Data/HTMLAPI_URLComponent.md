##### Data Type : HTML
##### HTMLAPI_URLComponent - HTMLAPI_URLComponent
---
```
#include <htmlapi.h>
```

**Definition :**
```
typedef union
{
	HTMLAPI_URLTargetComponent Target;
	HTMLAPI_URLArg  Arg;
} HTMLAPI_URLComponent;

```

**Description :**

To simplify memory management, the target components and args are unioned in one structure that can serve as the allocation unit for sequences (arrays) of target components and args.<br>



**Sample Usage :**
```
see sample html/convpic
```

**See Also :**
[HTMLAPIReference](/domino-c-api-docs/reference/Data/HTMLAPIReference)
[HTMLAPI_URLArg](/domino-c-api-docs/reference/Data/HTMLAPI_URLArg)
[HTMLAPI_URLTargetComponent](/domino-c-api-docs/reference/Data/HTMLAPI_URLTargetComponent)
---
