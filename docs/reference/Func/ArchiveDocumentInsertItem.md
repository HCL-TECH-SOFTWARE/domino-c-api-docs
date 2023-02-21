##### Function : archiving service
##### ArchiveDocumentInsertItem - Returns an extracted item back to an archive document instance.
---
```
#include <archsvc.h>
STATUS LNPUBLIC ArchiveDocumentInsertItem(

	HARCHIVEDOCUMENT  hArchDoc,
	ITEMINSERTCALLBACK  ItemInsertCallback,
	void *pUserCtx);
```
**Description :**

Note that item name is not specified as a parameter since it is included in the 
extracted data.

**Parameters :**
Input :
hArchDoc  -  Handle to archive document.

ItemInsertCallback  -  User supplied callback that returns item data to document.

pUserCtx  -  Caller-define context structure.

Output :
(routine)  -  NOERROR return status means that it is successful.



**See Also :**
[ITEMINSERTCALLBACK](/domino-c-api-docs/reference/Data/ITEMINSERTCALLBACK)
---
