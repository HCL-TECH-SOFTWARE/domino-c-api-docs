##### Data Type : Agents
##### CDACTIONDELETE - Delete action CD record.
---
```
#include <queryods.h>
```

**Definition :**
```
typedef struct {
   BSIG Header;
   DWORD dwFlags; /* flags */
} CDACTIONDELETE;
```

**Description :**

A CDACTIONDELETE record is stored in fields of type TYPE_ACTION, usually the action field of an Agent.  When the agent containing this action is run, the data selected by the agent is deleted.  The fields in this structure are:
<ul><br>

<ul><tt><font size="2">Header &nbsp;Defines this composite data item as a CDACTIONDELETE item.</font></tt><br>
<tt><font size="2">dwFlags Reserved; &nbsp;must be 0.</font></tt></ul>
</ul>



**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
