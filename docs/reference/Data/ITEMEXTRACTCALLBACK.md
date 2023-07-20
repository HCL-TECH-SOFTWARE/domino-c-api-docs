##### Data Type : archiving service
##### ITEMEXTRACTCALLBACK - User defined callback function for receiving item data from an archive document. 
---
```
#include <archsvc.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR ITEMEXTRACTCALLBACK)
	 (
	 const BYTE *Buffer,
	 DWORD dwBufferSize,
	 BOOL bLastBuffer,
	 STATUS retError,
	 void *pUserCtx
	 );
```

**Description :**

Note that the format of the item data exported is opaque and suitable for external storage.<br>
<br>
	Inputs:<br>
		Buffer - Contains a serialized item data.<br>
		BufferSize - Size of Buffer. <br>
		bLastBuffer - When TRUE, indicates that this is the last buffer of data for the current note.<br>
		pUserCtx - Caller-defined context structure.  <br>
	Returns:<br>
		NOERROR if successful, error status from lower level functions otherwise.


**See Also :**
[ArchiveDocumentExtractItem](/domino-c-api-docs/reference/Func/ArchiveDocumentExtractItem)
---
