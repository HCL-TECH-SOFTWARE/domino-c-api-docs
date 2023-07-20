##### Data Type : archiving service
##### ARCHIVETEXTOUTPUTCALLBACK - User supplied callback function used to return item data to ArchiveDocumentGetText.
---
```
#include <archsvc.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR ARCHIVETEXTOUTPUTCALLBACK)
	 (
	 const char *Text,
	 DWORD dwTextSize,
	 BOOL bLastBuffer, 
	 void *pUserCtx
	 );
```

**Description :**

	Inputs:<br>
		Text - Contains a serialized item data.<br>
		dwTextSize - Size of Text. <br>
		bLastBuffer - When TRUE, indicates that this is the last buffer of data for the current note.<br>
		pUserCtx - Caller-defined context structure.  <br>
	Returns:<br>
		NOERROR return status means that it is successful.


**See Also :**
[ArchiveDocumentGetText](/domino-c-api-docs/reference/Func/ArchiveDocumentGetText)
---
