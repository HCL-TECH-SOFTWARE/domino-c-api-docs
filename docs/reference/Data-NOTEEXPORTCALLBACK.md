##### Data Type : archiving service
##### NOTEEXPORTCALLBACK - User defined callback function for receiving notes document data.
---
##### #include <archsvc.h>
**Description :**
Note that the format of document data is opaque and suitable for external 
storage. Use ArchiveImportDocument to restore to an in-memory note for access 
to individual items. 

	Inputs:
	 Buffer - Contains a serialized notes document (or a partial stream 
depending on the size).
	 BufferSize - Size of Buffer. 
	 bLastBuffer - When TRUE, indicates that this is the last buffer of 
data for the current note.
	 pUserCtx - Caller-defined context structure.  
	Returns:
	 NOERROR if successful, error status from lower level functions 
otherwise.
**See Also :**
[ArchiveDocumentExport](D:/md_files/ArchiveDocumentExport.md)
---
