##### Function : Extension Manager
##### NSFArchiveCopyNotesEMCallback - Extension Manager callback for EM_NSFARCHIVECOPYNOTES.
---
```
#include <extmgr.h>
STATUS LNPUBLIC NSFArchiveCopyNotesEMCallback(

	DBHANDLE  hSrcDB,
	HANDLE  hDestDB,
	HANDLE  hIdTable,
	DWORD  dwFlags,
	TIMEDATE *ptdSrcMod,
	REPLFILESTATS *pStats);
```
**Description :**

EM_NSFARCHIVECOPYNOTES occurs when documents have been selected for archiving 
and copied from the source database to the specified destination database.  If  
registered with the EM_REG_BEFORE flag, the callback is called when the 
documents have been selected for archiving.  If registered with the 
EM_REG_AFTER flag, the callback is called after the documents have been copied 
from the source database to the specified destination database.

**Parameters :**
Input :
hSrcDB  -  dbhandle of the source database.

hDestDB  -  dbhandle of the destination database.

hIdTable  -  Handle to the id table containing the note ids to be copied to the destination.

dwFlags  -  None at this time.

ptdSrcMod  -  Pointer to a timedate for last modified time of source database.

pStats  -  Pointer to a REPLFILESTATS structure containing the stats of the copy.

Output :
(routine)  -  ERR_EM_CONTINUE -  Continue processing.  



**See Also :**
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
---
