##### Function : archiving service
##### ArchiveDocumentExport - Exports an archived document to a stream format.
---
```
#include <archsvc.h>
STATUS LNPUBLIC ArchiveDocumentExport(

	HARCHIVEDOCUMENT  hDoc,
	NOTEEXPORTCALLBACK  NoteExportCallback,
	void *pCtx);
```
**Description :**



**Parameters :**
Input :
hDoc  -  Handle to an archive document obtained via ArchiveExportDatabase.

NoteExportCallback  -  Callback function that receives serialzied note.

pCtx  -  Caller defined structure that is passed through to NoteExportCallback.

Output :
(routine)  -  NOERROR if successful, error status from lower level functions otherwise.



**See Also :**
[ARCHIVEDOCUMENTCALLBACK](/domino-c-api-docs/reference/Data/ARCHIVEDOCUMENTCALLBACK)
[NOTEEXPORTCALLBACK](/domino-c-api-docs/reference/Data/NOTEEXPORTCALLBACK)
---
