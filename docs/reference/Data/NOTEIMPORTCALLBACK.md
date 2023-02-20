##### Data Type : archiving service
##### NOTEIMPORTCALLBACK - User supplied callback function used to return notes export stream data to ArchiveImportDocument.
---
```
#include <archsvc.h>
```
**Description :**

This function may be called more than once for a document so implementors need 
to maintain context to account for this.

	Inputs:
	 MaxToRead - Amount of data requested.
	 pUserCtx - Caller-defined context structure.
	Outputs:
	 Buffer - Implementors should copy stream data to this buffer.  
	Returns:
	 Bytes written to Buffer.

**See Also :**
[ArchiveDocumentImport](/reference/Func/ArchiveDocumentImport)
---
