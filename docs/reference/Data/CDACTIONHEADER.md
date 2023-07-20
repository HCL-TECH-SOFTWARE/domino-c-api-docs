##### Data Type : Agents
##### CDACTIONHEADER - Action Header CD record.
---
```
#include <queryods.h>
```

**Definition :**
```
typedef struct {
   BSIG Header;
} CDACTIONHEADER;
```

**Description :**

The first record in a field of type TYPE_ACTION (usually the action field of an Agent) is a CDACTIONHEADER record, followed by CDACTION records identifying the actions to be performed.  The fields in this structure are:<br>

<ul>
<ul>Header		Defines this composite data item as a CDACTIONHEADER item.</ul>
</ul>



**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
