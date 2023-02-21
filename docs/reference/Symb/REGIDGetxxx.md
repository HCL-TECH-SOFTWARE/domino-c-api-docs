##### Symbolic Value : User Registration
##### REGIDGetxxx - Information type codes for ID files.
---
```
#include <reg.h>
```
**Description :**

Information type codes used by REGGetIDInfo() to identify the data items to be 
obtained from an ID file.

When an ID is made Safe, the Certifier, NotesExpress, and Desktop flags are 
cleared, so these flags will always be FALSE in a Safe copy.

Flat IDs do not distinguish between users and certifiers, so the Certifier flag 
will always be FALSE if the Hierarchical flag is FALSE.

**See Also :**
[REGGetIDInfo](/domino-c-api-docs/reference/Func/REGGetIDInfo)
---
