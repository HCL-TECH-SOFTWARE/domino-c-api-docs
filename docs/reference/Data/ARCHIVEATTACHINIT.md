##### Data Type : archiving service
##### ARCHIVEATTACHINIT - User-defined function called by ArchiveExportDatabase that indicates that an attachment is being sent. 
---
```
#include <archsvc.h>
```
**Description :**

Allows implementors to allocate space for accepting data, etc. Needed to accept 
data. 
	
	Inputs:
	 szFileName - This is the filename of the attachment.
	 dwFlags - Possible values are ARCHIVE_ATTACH_ENCRYPTED when the 
attachment is encrypted, look for ARCHIVE_ATTACH_xxx..
	 dwDupIdx - Used to differentiate multiple attachments with same name.
	 pUserCtx - Caller-defined context structure. 
	Returns:
	 NOERROR if successful, error status from lower level functions 
otherwise. 

**See Also :**
[ArchiveExportDatabase](/domino-c-api-docs/reference/Func/ArchiveExportDatabase)
[ARCHIVE_ATTACH_xxx](/domino-c-api-docs/reference/Symb/ARCHIVE_ATTACH_xxx)
---
