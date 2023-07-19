##### Data Type : Agents
##### CDACTIONREADMARKS - Modify Read Marks action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   BSIG  Header;
   DWORD dwFlags;
} CDACTIONREADMARKS;

**Description :**

This action CD record is stored in the TYPE_ACTION field of an Agent.  When this action record is encountered, the unread marks for the documents selected by the query segment of the Agent will either be set to Read (if the signature is SIG_ACTION_MARKREAD) or Unread (if the signature is SIG_ACTION_MARKUNREAD).


**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
