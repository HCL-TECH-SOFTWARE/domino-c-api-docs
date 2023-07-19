##### Data Type : Agents
##### CDACTIONREPLY - Create Reply action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD dwFlags;
   WORD  wBodyLen; /* Length of body text */
/* Body text follows */
} CDACTIONREPLY;

**Description :**

Create a reply message.  This record is stored in fields of type TYPE_ACTION, usually the action field of an Agent.  This record consists of the CDACTIONREPLY structure, followed by text for the body of the reply message.  The fields in this structure are:
<ul><br>

<ul>Header	Defines this composite data item as a CDACTIONREPLY item.<br>
dwFlags	Reply action flags (see ACTIONREPLY_FLAG_xxx).<br>
wBodyLen	Length of the body text in bytes.</ul>
<br>
This structure is followed by the body text.</ul>



**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
