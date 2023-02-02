##### Data Type : archiving service
##### ARCHIVETEXTOUTPUTCALLBACK - User supplied callback function used to return item data to ArchiveDocumentGetText.
---
##### #include <archsvc.h>
**Description :**
	Inputs:
	 Text - Contains a serialized item data.
	 dwTextSize - Size of Text. 
	 bLastBuffer - When TRUE, indicates that this is the last buffer of 
data for the current note.
	 pUserCtx - Caller-defined context structure.  
	Returns:
	 NOERROR return status means that it is successful.
**See Also :**
[ArchiveDocumentGetText](D:/md_files/ArchiveDocumentGetText.md)
---
