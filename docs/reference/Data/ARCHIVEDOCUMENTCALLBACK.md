##### Data Type : archiving service
##### ARCHIVEDOCUMENTCALLBACK - User-defined function called by ArchiveExportDatabase that used to pass an archive document to the implementor.
---
```
#include <archsvc.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR ARCHIVEDOCUMENTCALLBACK)
	 (
	 HARCHIVEDOCUMENT hArchDoc,
	 void *pUserCtx);

**Description :**

Implementors must call ArchiveDocumentDestroy when finished to free resources.<br>
<br>
	Inputs: <br>
		hArchDoc - Handle to archive document.<br>
  		pUserCtx - Caller-defined context structure. <br>
       Return:<br>
              NOERROR return status means that it is successful.


**See Also :**
[ArchiveDocumentExport](/domino-c-api-docs/reference/Func/ArchiveDocumentExport)
[ArchiveExportDatabase](/domino-c-api-docs/reference/Func/ArchiveExportDatabase)
---
