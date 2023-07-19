##### Data Type : Agents
##### CDACTIONFORMULA - Formula action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD dwFlags;
   WORD  wFormulaLen; /* Length of formula */
	 /* Formula follows */
} CDACTIONFORMULA;

**Description :**

A CDACTIONFORMULA record is stored in fields of type TYPE_ACTION, usually the action field of an Agent. When the agent containing this action is run, the formula is evaluated using the data selected by the agent.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDACTIONFORMULA item.<br>
dwFlags	Option flags (see ACTIONFORMULA_FLAG_xxx).<br>
wFormulaLen	Length of the formula.</ul>
<br>
This structure is followed by the formula.</ul>



**See Also :**
[ACTIONFORMULA_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTIONFORMULA_FLAG_xxx)
---
