##### Data Type : archiving service
##### ARCHIVEDOCUMENTCALLBACK - User-defined function called by ArchiveExportDatabase that used to pass an archive document to the implementor.
---
##### #include <archsvc.h>
**Description :**
Implementors must call ArchiveDocumentDestroy when finished to free resources.

	Inputs: 
	 hArchDoc - Handle to archive document.
    pUserCtx - Caller-defined context structure. 
       Return:
              NOERROR return status means that it is successful.
**See Also :**
[ArchiveDocumentExport](D:/md_files/ArchiveDocumentExport.md)
[ArchiveExportDatabase](D:/md_files/ArchiveExportDatabase.md)
---
