##### Data Type : Item (Field) Information
##### LIST - Used to specify multiple values in a field.
---
```
#include <global.h>
```

**Definition :**

typedef struct {
   USHORT ListEntries;
/* now come the list entries */
} LIST;

**Description :**

This datatype is used by several data structures to specify that a field contains a list of one or more values.  A list is made up of one or more items of a datatype, separated by a delimiter.<br>
<br>
The value in the ListEntries field of LIST is the number of items specified in a delimited list of items.<br>



**See Also :**
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
[TYPE_xxx [TEXT_LIST]](/domino-c-api-docs/reference/Symb/TYPE_xxx [TEXT_LIST])
---
