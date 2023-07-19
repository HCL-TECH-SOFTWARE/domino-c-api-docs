##### Symbolic Value : Constants
##### ACTION_SYS_CMD_xxx - Action system commands.
---
```
#include <actprop.h>
```

**Symbolic Values :**

	ACTION_SYS_CMD_CATEGORIZE	  -  Put a document in a category.

	ACTION_SYS_CMD_EDIT	  -  Open a document in edit mode.

	ACTION_SYS_CMD_SEND	  -  Send a document to the address specified in the document's "SendTo" field. if there is no "SendTo" field in the document, use ACTION_SYS_CMD_FORWARD.

	ACTION_SYS_CMD_FORWARD	  -  Forward a document. Use this option if there is no "SendTo" field in the document.

	ACTION_SYS_CMD_MOVE_TO_FOLDER	  -  Put a document in a folder.

	ACTION_SYS_CMD_REMOVE_FROM_FOLDER	  -  Remove a document from a folder.


**Description :**

Action system commands.  If you set ACTION_SYS_COMMAND as the value for the Type member of CDACTION, set the second word of  the variable action data to one of these values. Please see the Tech Note &quot;<a href="/apiref.nsf/61fd4e9848264ad28525620b006ba8bd/76189a185bacf654852563b1006a7e8c?OpenDocument"><u><font color="#008000">System Action Command Codes</font></u></a>&quot; for more details.


**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
