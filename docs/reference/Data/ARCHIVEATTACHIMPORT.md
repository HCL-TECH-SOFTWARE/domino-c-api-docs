##### Data Type : archiving service
##### ARCHIVEATTACHIMPORT - User-supplied function used to return attachment data to ArchiveRestoreDocument.
---
```
#include <archsvc.h>
```
**Description :**

	Inputs:
	 FileName - Name of the attachment.
	 FileNameLen - Length of FileName.
	 dwDupIdx - Differentiates attachments when multiple files with same 
name.
	 MaxToRead - Number of bytes being requested.
	 pUserCtx - Caller-defined context structure.
	Outputs:
	 Buffer - Implementors should copy attachment data to this buffer.  
	Returns:
	 NOERROR return status means that it is successful.

**See Also :**
[ArchiveRestoreDocument](/reference/Func/ArchiveRestoreDocument)
---
