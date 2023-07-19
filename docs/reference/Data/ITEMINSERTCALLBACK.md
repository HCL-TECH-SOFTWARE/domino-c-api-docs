##### Data Type : archiving service
##### ITEMINSERTCALLBACK - User supplied callback function used to return extracted item data to ArchiveDocumentInsertItem.
---
```
#include <archsvc.h>
 ITEMINSERTCALLBACK(
void);
```

**Definition :**

typedef DWORD (LNCALLBACKPTR ITEMINSERTCALLBACK)
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


**Parameters :**




**See Also :**
[ArchiveDocumentInsertItem](/domino-c-api-docs/reference/Func/ArchiveDocumentInsertItem)
---
