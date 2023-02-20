##### Function : archiving service
##### ArchiveDocumentImport - Creates an ArchiveDocument from a previously exported stream.
---
```
#include <archsvc.h>
STATUS LNPUBLIC ArchiveDocumentImport(

	DWORD  Flags,
	NOTEIMPORTCALLBACK  NoteImportCallback,
	void *pUserCtx,
	HARCHIVEDOCUMENT *phArchDoc);
```
**Description :**



**Parameters :**
Input :
Flags  -  Unused. Please set 0.

NoteImportCallback  -  Caller defined function that returns exported note data in the supplied buffer.

pUserCtx  -  Caller-defined context structure.

Output :
(routine)  -  NOERROR if successful, error status from lower level functions otherwise.


phArchDoc  -  Pointer to created ArchiveDocument. Callers should free the created document with ArchiveDocumentDestroy.


**See Also :**
[ArchiveRestoreDocument](/reference/Func/ArchiveRestoreDocument)
[ArchiveRestoreDocumentToNote](/reference/Func/ArchiveRestoreDocumentToNote)
[NOTEIMPORTCALLBACK](/reference/Data/NOTEIMPORTCALLBACK)
---
