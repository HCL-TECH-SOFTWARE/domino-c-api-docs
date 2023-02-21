##### Data Type : archiving service
##### ITEMEXTRACTCALLBACK - User defined callback function for receiving item data from an archive document. 
---
```
#include <archsvc.h>
```
**Description :**

Note that the format of the item data exported is opaque and suitable for 
external storage.

	Inputs:
	 Buffer - Contains a serialized item data.
	 BufferSize - Size of Buffer. 
	 bLastBuffer - When TRUE, indicates that this is the last buffer of 
data for the current note.
	 pUserCtx - Caller-defined context structure.  
	Returns:
	 NOERROR if successful, error status from lower level functions 
otherwise.

**See Also :**
[ArchiveDocumentExtractItem](/domino-c-api-docs/reference/Func/ArchiveDocumentExtractItem)
---
