##### Data Type : archiving service
##### ITEMINSERTCALLBACK - User supplied callback function used to return extracted item data to ArchiveDocumentInsertItem.
---
##### #include <archsvc.h>
 **ITEMINSERTCALLBACK(**
void);
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
**Parameters :**


**See Also :**
[ArchiveDocumentInsertItem](D:/md_files/ArchiveDocumentInsertItem.md)
---
