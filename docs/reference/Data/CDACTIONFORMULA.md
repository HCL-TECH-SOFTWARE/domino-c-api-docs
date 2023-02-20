##### Data Type : Agents
##### CDACTIONFORMULA - Formula action CD record.
---
```
#include <queryods.h>
```
**Description :**

A CDACTIONFORMULA record is stored in fields of type TYPE_ACTION, usually the 
action field of an Agent. When the agent containing this action is run, the 
formula is evaluated using the data selected by the agent.  The fields in this 
structure are:

Header  Defines this composite data item as a CDACTIONFORMULA item.
dwFlags Option flags (see ACTIONFORMULA_FLAG_xxx).
wFormulaLen Length of the formula.

This structure is followed by the formula.


**See Also :**
[ACTIONFORMULA_FLAG_xxx](/reference/Symb/ACTIONFORMULA_FLAG_xxx)
---
