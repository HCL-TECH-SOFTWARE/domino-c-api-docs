##### Symbolic Value : Error Handling
##### NOERROR - Function return STATUS code indicating "success".
---
```
#include <globerr.h>
```

**Symbolic Values :**



**Description :**

Many API functions return a value of type STATUS.  A return value of NOERROR indicates success.  The value of NOERROR is 0 so that the following expression is more readable:<br>
<br>
<br>
    if (error = NotesAPIFunction(...))<br>
        return(error);


**See Also :**
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
---
