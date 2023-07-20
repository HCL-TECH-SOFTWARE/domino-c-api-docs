##### Data Type : Agents
##### CDACTIONMODIFYFIELD - Modify Field action CD Record.
---
```
#include <queryods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;
   DWORD dwFlags;      /* flags MODIFYFIELD_FLAG_xxx */
 WORD wFieldNameLen; /* Length of field name to modify */
 WORD wValueLen;     /* Length of new value */
	 /* Field name follows */
	 /* Value follows */
} CDACTIONMODIFYFIELD;
```

**Description :**

A CDACTIONMODIFYFIELD record is stored in fields of type TYPE_ACTION, usually the action field of an Agent.  When the agent containing this action is run, the value of the specified field is modified in the notes selected by the Agent.  The fields in this structure are:
<ul><br>

<ul><tt><font size="2">Header &nbsp; &nbsp; &nbsp; &nbsp; Defines this composite data item as a</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;CDACTIONMODIFYFIELD item.</font></tt><br>
<tt><font size="2">dwFlags &nbsp; &nbsp; &nbsp; &nbsp;Option flags (see MODIFYFIELD_FLAG_xxx)</font></tt><br>
<tt><font size="2">wFieldNameLen &nbsp;Length of the field name.</font></tt><br>
<tt><font size="2">wValueLen &nbsp; &nbsp; &nbsp;Length of the new value.</font></tt></ul>
<br>
This structure is followed by packed strings containing the field name and the new value for the field.</ul>



**See Also :**
[MODIFYFIELD_FLAG_xxx](/domino-c-api-docs/reference/Symb/MODIFYFIELD_FLAG_xxx)
---
