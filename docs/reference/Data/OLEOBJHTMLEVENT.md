##### Data Type : HTML
##### OLEOBJHTMLEVENT - HTML Object event entry.
---
```
#include <oleods.h>
```

**Definition :**
```
typedef struct {
   WORD wLength;        /* Size of this structure including both
                           fixed and variable sections */
   WORD wsNameLength;   /* Length of Name */
   WORD wsScriptLength; /* Length of Script */
   WORD wReserved1;     /* Unused, must be 0 */
   WORD wReserved2;     /* Unused, must be 0 */
/*
   The variable length portions go here in the following order:
   Name
   Script 
*/
} OLEOBJHTMLEVENT;
```

**Description :**




**See Also :**
[OLEOBJHTMLDATA](/domino-c-api-docs/reference/Data/OLEOBJHTMLDATA)
[OLEOBJHTMLEVENT](/domino-c-api-docs/reference/Data/OLEOBJHTMLEVENT)
---
