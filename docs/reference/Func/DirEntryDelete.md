##### Function : Dir
##### DirEntryDelete - Helper functions for the DirModify fields of the DirEntry. 
---
```
#include <direntry.h>
STATUS LNPUBLIC DirEntryDelete(

	DIRENTRY  hEntry);
```
**Description :**

Delete the Domino entry in the directory which is associated with hEntry. If 
the entry exists in a Domino directory then it is deleted. If it exists in an 
LDAP directory then only the Domino specific items are deleted from the entry.

**Parameters :**
Input :
hEntry  -  Handle to the entry to delete.

Output :
(routine)  -  NOERROR 
An ERR status on failure indicating the problem. 




**See Also :**
[DirCtxGetEntryByID](/domino-c-api-docs/reference/Func/DirCtxGetEntryByID)
---
