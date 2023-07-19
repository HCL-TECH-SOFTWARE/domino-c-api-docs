##### Data Type : archiving service
##### ARCHIVEATTACHIMPORT - User-supplied function used to return attachment data to ArchiveRestoreDocument.
---
```
#include <archsvc.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR ARCHIVEATTACHIMPORT)
	(const char *FileName,
	DWORD FileNameLen,
	DWORD dwDupIdx,
	BYTE *Buffer,
	DWORD MaxToRead,
	void *pUserCtx);

**Description :**

	Inputs:<br>
		FileName - Name of the attachment.<br>
		FileNameLen - Length of FileName.<br>
		dwDupIdx - Differentiates attachments when multiple files with same name.<br>
		MaxToRead - Number of bytes being requested.<br>
		pUserCtx - Caller-defined context structure.<br>
	Outputs:<br>
		Buffer - Implementors should copy attachment data to this buffer. 	<br>
	Returns:<br>
		NOERROR return status means that it is successful.


**See Also :**
[ArchiveRestoreDocument](/domino-c-api-docs/reference/Func/ArchiveRestoreDocument)
---
