##### Data Type : Notes/FX data
##### NOTES_EXECUTE_DOCACTION_MSG - Used by OLE server to request Notes to perform an action.
---
```
#include <olenotes.h>
```

**Definition :**

typedef struct {
   int ActionID;    /* Doc action ID for Notes to process */
   DWORD Flags;     /* Reserved;  must be 0 */
   DWORD Unused[3]; /* Reserved;  must be 0 */
} NOTES_EXECUTE_DOCACTION_MSG;

**Description :**

This data structure is passed by an OLE server to Notes in response to an OLE request for data in the NotesDocAction format.


**See Also :**
[NOTES_DOC_INFO_MSG](/domino-c-api-docs/reference/Data/NOTES_DOC_INFO_MSG)
[DOC_ACTION_INFO](/domino-c-api-docs/reference/Data/DOC_ACTION_INFO)
---
