##### Function : archiving service
##### ArchiveRestoreDocument - Restores a note back to the specified database.
---
```
#include <archsvc.h>
STATUS LNPUBLIC ArchiveRestoreDocument(

	DBHANDLE  hDb,
	DWORD  Flags,
	HARCHIVEDOCUMENT  hArchDoc,
	ARCHIVEATTACHIMPORT  AttachImportCallback,
	void *pUserCtx,
	NOTEHANDLE *hNote);
```
**Description :**

ArchiveRestoreDocument writes a note and its related attachments to the 
caller-specified database replacing any note that may currently exist with the 
same UNID. 

**Parameters :**
Input :
hDb  -  Handle to target database.

Flags  -  Unused. Please set 0.

hArchDoc  -  Handle to archive document. See ArchiveDocumentImport for details on obtaining an archive document handle. 

AttachImportCallback  -  Caller defined function that returns attachment data in the supplied buffer.

pUserCtx  -  Caller-defined context structure.

Output :
(routine)  -  NOERROR if successful, error status ERR_ARCHIVE_IMPORT_UNEXPECTED_EOD if incomplete data stream returned. from lower level functions otherwise.


hNote  -  Handle to note created from export stream.


**See Also :**
[ARCHIVEATTACHIMPORT](/domino-c-api-docs/reference/Data/ARCHIVEATTACHIMPORT)
[ArchiveDocumentImport](/domino-c-api-docs/reference/Func/ArchiveDocumentImport)
[HARCHIVEDOCUMENT](/domino-c-api-docs/reference/Data/HARCHIVEDOCUMENT)
---
