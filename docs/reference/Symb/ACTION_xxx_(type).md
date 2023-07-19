##### Symbolic Value : Form
##### ACTION_xxx (type) - CDACTION Type.
---
```
#include <actprop.h>
```

**Symbolic Values :**

	ACTION_RUN_FORMULA	  -  Formula ActionType.

	ACTION_RUN_SCRIPT	  -  Script Action Type.

	ACTION_RUN_AGENT	  -  Agent Action Type.

	ACTION_OLDSYS_COMMAND	  -  System Command Action Type.

	ACTION_SYS_COMMAND	  -  System Command Action Type.

	ACTION_PLACEHOLDER	  -  Place holder for Action Type.

	ACTION_RUN_JAVASCRIPT	  -  Java Script Action Type.


**Description :**

The CDACTION structure contains an action Type member of one of the above.<br>
<br>
       ACTION_RUN_JAVASCRIPT is an V5 Action Type, and the CD record of this type should be defined in the rich-text item &quot;$V5ACTIONS&quot;, not the &quot;$ACTIONS&quot;.


**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
