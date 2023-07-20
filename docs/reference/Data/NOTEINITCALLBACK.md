##### Data Type : archiving service
##### NOTEINITCALLBACK - User-defined function called by ArchiveExportDatabase that indicates the beginning of a document export sequence.
---
```
#include <archsvc.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR NOTEINITCALLBACK)
	(
	NOTEHANDLE hNote,
	STATUS retError,
	void *pUserCtx
	);
```

**Description :**

This provides the implementor with an opportunity to allocate space or perform other initializations needed to accept a document and its attachment data.<br>
<br>
	Inputs: <br>
		hNote - Handle to the note being streamed to the caller.<br>
  		pUserCtx - Caller-defined context structure. <br>
	Returns:<br>
		NOERROR if implementor wants to process note, Returning any other non-zero error status will stop all processing. 


**See Also :**
[ArchiveExportDatabase](/domino-c-api-docs/reference/Func/ArchiveExportDatabase)
---
