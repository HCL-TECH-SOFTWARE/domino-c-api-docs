##### Data Type : HTML
##### CmdArgValueType - Domino Command Argument Value Types (CAVT)
---
```
#include <htmlapi.h>
```

**Definition :**

typedef enum
{
    CAVT_String     = 0,    /* arg value is a pointer to a nul-terminated 
string */
    CAVT_Int        = 1,    /* arg value is an int */
    CAVT_NoteId     = 2,    /* arg value is a NOTEID */
    CAVT_UNID       = 3,    /* arg value is an UNID */
    CAVT_StringList = 4     /* arg value is a list of null-terminated strings */

} CmdArgValueType;


**Description :**

In the HTML reference, there exist URL commands, and there are arguments associated with those URL commands.This Data structure tells all the Domino Command Argument Value Types 


**See Also :**
---
