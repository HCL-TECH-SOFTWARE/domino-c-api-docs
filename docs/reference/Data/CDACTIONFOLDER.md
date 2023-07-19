##### Data Type : Agents
##### CDACTIONFOLDER - Folder action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD dwFlags;        /* flags */
   WORD  wFolderNameLen; /* length of folder name */
   WORD  wSpare;
	 /* folder name follows */
} CDACTIONFOLDER;

**Description :**

A CDACTIONFOLDER record is stored in fields of type TYPE_ACTION, usually the action field of an Agent.  The action depends on the signature.  SIG_ACTION_MOVETOFOLDER indicates that the data selected by the agent is to be placed in the folder and deleted from the original location.  SIG_ACTION_COPYTOFOLDER indicates that a copy of the data selected by the agent is to be placed in the folder.  SIG_ACTION_REMOVEFROMFOLDER indicates that the data selected by the agent is to be removed from the folder.  The fields in this structure are:
<ul><br>
<br>
Header			Defines this composite data item as a CDACTIONFOLDER item.<br>
dwFlags		Option flags (see ACTIONFOLDER_FLAG_xxx)<br>
wFolderNameLen	Length of the folder name<br>
wSpare			Reserved;  must be 0.<br>
<br>
This structure is followed by a packed string containing the folder name.</ul>



**See Also :**
[ACTIONFOLDER_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTIONFOLDER_FLAG_xxx)
---
