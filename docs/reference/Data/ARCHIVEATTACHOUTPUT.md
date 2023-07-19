##### Data Type : archiving service
##### ARCHIVEATTACHOUTPUT - User-defined function called by ArchiveExportDatabase that used to pass attachment data to the implementor.
---
```
#include <archsvc.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR ARCHIVEATTACHOUTPUT)
	 (
	 const BYTE *Buffer,
	 DWORD BufferSize,
	 BOOL bLastBuffer,
	 STATUS retError,
	 void *pUserCtx);

**Description :**

Can be called many times for each attachment.<br>
	Inputs:<br>
		Buffer - Contains attachment data.<br>
		BufferSize - Size of Buffer.<br>
		bLastBuffer - TRUE when we are sending the last buffer.<br>
		pUserCtx - Caller-defined context structure.<br>
	Returns:<br>
		NOERROR if successful, error status from lower level functions otherwise.


**See Also :**
[ARCHIVEATTACHINIT](/domino-c-api-docs/reference/Data/ARCHIVEATTACHINIT)
[ArchiveExportDatabase](/domino-c-api-docs/reference/Func/ArchiveExportDatabase)
---
