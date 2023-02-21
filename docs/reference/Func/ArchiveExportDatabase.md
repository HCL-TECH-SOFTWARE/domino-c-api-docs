##### Function : archiving service
##### ArchiveExportDatabase - Exports a set of documents from a database to user supplied callbacks. 
---
```
#include <archsvc.h>
STATUS LNPUBLIC ArchiveExportDatabase(

	DBHANDLE  hDb,
	DHANDLE  hIDTable,
	DWORD  Flags,
	NOTEINITCALLBACK  NoteInitCallback,
	ARCHIVEATTACHINIT  AttachInitCallback,
	ARCHIVEATTACHOUTPUT  AttachOutputCallback,
	ARCHIVEDOCUMENTCALLBACK  ArchiveDocumentCallback,
	KFHANDLE  hKFC,
	void *pUserCtx);
```
**Description :**

The ArchiveExportDatabase function copies notes and their related attachments 
from a database and passes the exported data to callers via a set of callback 
functions. Callbacks occur in the order that they appear in the function 
declaration. Attachments are decompressed so that they may be consumed by 
programs that understand their native format. Notes documents are encoded into 
a canonical format that is opaque to the caller but can be manipulated in a 
limited way by the Archiving Services API. 

**Parameters :**
Input :
hDb  -  Handle to source database.

hIDTable  -  Handle to IDTable indicating the notes to be exported.

Flags  -  Flags that control optional behavior (None defined at this point).

NoteInitCallback  -  Called for every note that is streamed to the caller. Gives the implementor an opportunity to allocate space, etc. needed for the data.

AttachInitCallback  -  User supplied callback that is called to indicate that a file attachment is being sent. 

AttachOutputCallback  -  User supplied callback that receives attachment data.

ArchiveDocumentCallback  -  User supplied callback that receives a Notes document in stream format.(See NOTEEXPORTCALLBACK for more details)

hKFC  -  Needed to decrypt encrypted notes. Handle for ID File. Pass null for current user ID.

pUserCtx  -  Caller-defined context structure.

Output :
(routine)  -  NOERROR if successful, error status from lower level functions otherwise.



**See Also :**
[ARCHIVEATTACHINIT](/domino-c-api-docs/reference/Data/ARCHIVEATTACHINIT)
[ARCHIVEATTACHOUTPUT](/domino-c-api-docs/reference/Data/ARCHIVEATTACHOUTPUT)
[ARCHIVEDOCUMENTCALLBACK](/domino-c-api-docs/reference/Data/ARCHIVEDOCUMENTCALLBACK)
[NOTEINITCALLBACK](/domino-c-api-docs/reference/Data/NOTEINITCALLBACK)
---
