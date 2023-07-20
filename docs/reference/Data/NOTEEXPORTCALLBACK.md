##### Data Type : archiving service
##### NOTEEXPORTCALLBACK - User defined callback function for receiving notes document data.
---
```
#include <archsvc.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR NOTEEXPORTCALLBACK)
	 (
	 const BYTE *Buffer,
	 DWORD dwBufferSize,
	 BOOL bLastBuffer, 
	 STATUS retError,
	 void *pUserCtx
	 );
```

**Description :**

Note that the format of document data is opaque and suitable for external storage. Use ArchiveImportDocument to restore to an in-memory note for access to individual items. <br>
<br>
	Inputs:<br>
		Buffer - Contains a serialized notes document (or a partial stream depending on the size).<br>
		BufferSize - Size of Buffer. <br>
		bLastBuffer - When TRUE, indicates that this is the last buffer of data for the current note.<br>
		pUserCtx - Caller-defined context structure.  <br>
	Returns:<br>
		NOERROR if successful, error status from lower level functions otherwise.


**See Also :**
[ArchiveDocumentExport](/domino-c-api-docs/reference/Func/ArchiveDocumentExport)
---
