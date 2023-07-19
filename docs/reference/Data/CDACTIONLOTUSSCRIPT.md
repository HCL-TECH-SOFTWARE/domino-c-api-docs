##### Data Type : Agents
##### CDACTIONLOTUSSCRIPT - LotusScript action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD dwFlags;
   DWORD dwScriptLen; /* Length of script */
	 /* Script follows */
} CDACTIONLOTUSSCRIPT;

**Description :**

A CDACTIONLOTUSSCRIPT record is stored in fields of type TYPE_ACTION, such as in the action field of an Agent.  This record contains LotusScript commands that will be executed when the agent is run.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDACTIONLOTUSSCRIPT item.<br>
dwFlags	Option flags - reserved;  must be 0.<br>
wScriptLen	Length of LotusScript commands.</ul>
<br>
This structure is followed by the LotusScript commands.</ul>



**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
