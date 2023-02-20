##### Data Type : Agents
##### CDACTIONREPLY - Create Reply action CD record.
---
```
#include <queryods.h>
```
**Description :**

Create a reply message.  This record is stored in fields of type TYPE_ACTION, 
usually the action field of an Agent.  This record consists of the 
CDACTIONREPLY structure, followed by text for the body of the reply message.  
The fields in this structure are:

Header Defines this composite data item as a CDACTIONREPLY item.
dwFlags Reply action flags (see ACTIONREPLY_FLAG_xxx).
wBodyLen Length of the body text in bytes.

This structure is followed by the body text.


**See Also :**
[CDACTION](/reference/Data/CDACTION)
---
