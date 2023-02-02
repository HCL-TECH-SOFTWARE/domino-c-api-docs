##### Function : archiving service
##### ArchiveRestoreDocumentToNote - Returns an exported notes document to an open note.
---
##### #include <archsvc.h>
STATUS LNPUBLIC **ArchiveRestoreDocumentToNote(**

	NOTEHANDLE  hTargetNote,
	DWORD  Flags,
	HARCHIVEDOCUMENT  hArchDoc,
	void *pUserCtx);
**Description :**
ArchiveRestoreDocumentToNote returns the exported note data to an open note 
supplied by the caller. It does not restore attachments and thus care needs to 
be taken to ensure that either the note is not saved to the database or 
attachments are restored and references to attachments in the note are adjusted 
accordingly.
**Parameters :**
Input :
hTargetNote  -  Handle to target note.

Flags  -  Unused. Please set 0.

hArchDoc  -  Handle to archive document. See ArchiveDocumentImport for details on obtaining an archive document handle.

pUserCtx  -  Caller-defined context structure. 

Output :
(routine)  -  NOERROR if successful, error status ERR_ARCHIVE_IMPORT_UNEXPECTED_EOD if incomplete data stream returned. from lower level functions otherwise.


**See Also :**
[ArchiveDocumentImport](D:/md_files/ArchiveDocumentImport.md)
[HARCHIVEDOCUMENT](D:/md_files/HARCHIVEDOCUMENT.md)
---
