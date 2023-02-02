##### Function : Extension Manager
##### NSFArchiveDeleteNotesEMCallback - Extension Manager callback for EM_NSFARCHIVEDELETENOTES
---
##### #include <extmgr.h>
STATUS LNPUBLIC **NSFArchiveDeleteNotesEMCallback(**

	DBHANDLE  hDB,
	HANDLE  hTempIDTable,
	DWORD  dwFlags);
**Description :**
EM_NSFARCHIVEDELETENOTES is called after documents have been selected and 
copied to the destination database and it is time for archiving to delete the 
archived notes that qualify from the source database.   If  registered with the 
EM_REG_BEFORE flag, the callback is called before the documents are deleted 
from the source database.  If registered with the EM_REG_AFTER flag, the 
callback is called after the documents have been deleted from the source 
database.
**Parameters :**
Input :
hDB  -  Handle of the source database where notes will be deleted from.

hTempIDTable  -  Handle of the id table containing the notes ids to be deleted.

dwFlags  -  None at this time.

Output :
(routine)  -  ERR_EM_CONTINUE -  Continue processing.  


**See Also :**
[EM_xxx](D:/md_files/EM_xxx.md)
---
