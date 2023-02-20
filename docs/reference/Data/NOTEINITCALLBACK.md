##### Data Type : archiving service
##### NOTEINITCALLBACK - User-defined function called by ArchiveExportDatabase that indicates the beginning of a document export sequence.
---
```
#include <archsvc.h>
```
**Description :**

This provides the implementor with an opportunity to allocate space or perform 
other initializations needed to accept a document and its attachment data.

	Inputs: 
	 hNote - Handle to the note being streamed to the caller.
    pUserCtx - Caller-defined context structure. 
	Returns:
	 NOERROR if implementor wants to process note, Returning any other 
non-zero error status will stop all processing. 

**See Also :**
[ArchiveExportDatabase](/reference/Func/ArchiveExportDatabase)
---
