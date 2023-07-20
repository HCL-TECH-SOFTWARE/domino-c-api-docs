##### Data Type : archiving service
##### ARCHIVEATTACHINIT - User-defined function called by ArchiveExportDatabase that indicates that an attachment is being sent. 
---
```
#include <archsvc.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR ARCHIVEATTACHINIT)
	 (
	 const char *szFileName,
	 DWORD dwFlags,
	 DWORD dwDupIdx,
	 STATUS retError,
	 void *pUserCtx);
```

**Description :**

Allows implementors to allocate space for accepting data, etc. Needed to accept data. <br>
	<br>
	Inputs:<br>
		szFileName - This is the filename of the attachment.<br>
		dwFlags - Possible values are ARCHIVE_ATTACH_ENCRYPTED when the attachment is encrypted, look for ARCHIVE_ATTACH_xxx..<br>
		dwDupIdx - Used to differentiate multiple attachments with same name.<br>
		pUserCtx - Caller-defined context structure.	<br>
	Returns:<br>
		NOERROR if successful, error status from lower level functions otherwise. 


**See Also :**
[ArchiveExportDatabase](/domino-c-api-docs/reference/Func/ArchiveExportDatabase)
[ARCHIVE_ATTACH_xxx](/domino-c-api-docs/reference/Symb/ARCHIVE_ATTACH_xxx)
---
