##### Data Type : archiving service
##### NOTEIMPORTCALLBACK - User supplied callback function used to return notes export stream data to ArchiveImportDocument.
---
```
#include <archsvc.h>
```

**Definition :**

typedef DWORD (LNCALLBACKPTR NOTEIMPORTCALLBACK)
	(BYTE *Buffer,
	DWORD MaxToRead,
	void *pUserCtx);

**Description :**

This function may be called more than once for a document so implementors need to maintain context to account for this.<br>
<br>
	Inputs:<br>
		MaxToRead - Amount of data requested.<br>
		pUserCtx - Caller-defined context structure.<br>
	Outputs:<br>
		Buffer - Implementors should copy stream data to this buffer.  <br>
	Returns:<br>
		Bytes written to Buffer.


**See Also :**
[ArchiveDocumentImport](/domino-c-api-docs/reference/Func/ArchiveDocumentImport)
---
