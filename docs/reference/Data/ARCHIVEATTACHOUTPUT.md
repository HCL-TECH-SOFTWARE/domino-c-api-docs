##### Data Type : archiving service
##### ARCHIVEATTACHOUTPUT - User-defined function called by ArchiveExportDatabase that used to pass attachment data to the implementor.
---
```
#include <archsvc.h>
```
**Description :**

Can be called many times for each attachment.
	Inputs:
	 Buffer - Contains attachment data.
	 BufferSize - Size of Buffer.
	 bLastBuffer - TRUE when we are sending the last buffer.
	 pUserCtx - Caller-defined context structure.
	Returns:
	 NOERROR if successful, error status from lower level functions 
otherwise.

**See Also :**
[ARCHIVEATTACHINIT](/reference/Data/ARCHIVEATTACHINIT)
[ArchiveExportDatabase](/reference/Func/ArchiveExportDatabase)
---
