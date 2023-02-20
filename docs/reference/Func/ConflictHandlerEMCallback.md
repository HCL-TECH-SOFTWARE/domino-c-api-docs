##### Function : Extension Manager
##### ConflictHandlerEMCallback - Extension Manager callback for EM_NSFCONFLICTHANDLER
---
```
#include <extmgr.h>
STATUS LNPUBLIC ConflictHandlerEMCallback(

	HANDLE  hDb,
	HANDLE  hOldNote,
	HANDLE  hNewNote,
	DWORD *pAction);
```
**Description :**

EM_NSFCONFLICTHANDLER notifies you that a replication conflict has occurred.

**Parameters :**
Input :
hDb  -  Database Handle

hOldNote  -  Original Note Handle

hNewNote  -  New Note Handle

Output :
(routine)  -  
ERR_EM_CONTINUE


pAction  -  
CONFLICT_ACTION_MERGE - Have Domino or Notes try to merge
CONFLICT_ACTION_HANDLE - User handled the conflict
(zero) - Proceed with Conflict in normal manner


**See Also :**
[EM_xxx](/reference/Symb/EM_xxx)
---
