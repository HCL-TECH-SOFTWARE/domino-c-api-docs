##### Data Type : Agents
##### CDACTIONSENDDOCUMENT - Send Document action CD record.
---
```
#include <queryods.h>
```

**Definition :**
```
typedef struct {
   BSIG Header;
   DWORD dwFlags;
} CDACTIONSENDDOCUMENT;
```

**Description :**

The Send Document action is stored in a CDACTIONSENDDOCUMENT record in fields of type TYPE_ACTION, usually the action field of an Agent.  The fields in this structure are:
<ul><br>

<ul>Header			Defines this composite data item as a CDACTIONSENDDOCUMENT item.<br>
dwFlags		Reserved;  must be 0.</ul>
</ul>



**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
