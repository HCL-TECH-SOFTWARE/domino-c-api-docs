##### Function : OLE
##### NSFNoteOLEDisassociateFileFromObject - Disassociate an attachment ($FILE) from an OLE object.
---
##### #include <nsfasc.h>
STATUS LNPUBLIC **NSFNoteOLEDisassociateFileFromObject(**

	NOTEHANDLE  hNote,
	char *pszObjName,
	char *pszAttachmentName);
**Description :**
Disassociate an attachment ($FILE) from an OLE object.
**Parameters :**
Input :
hNote  -  Handle of the OLE object's note.

pszObjName  -  Pointer to name of the OLE object.

pszAttachmentName  -  Pointer to the name of the attachment to disassociate.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_ARGS_INVALID - A required argument (hNote, pszObjName, pszAttachmentName) was not supplied.

ERR_ASSOCITEM_NOITEMS - There are no files associated with the OLE object.

ERR_xxx - STATUS returned from a lower level Notes function call.  Use OSLoadString and display/log the error.


**See Also :**
[NSFNoteOLEAssociateFileToObject](D:/md_files/NSFNoteOLEAssociateFileToObject.md)
[NSFNoteOLEGetAssociateFileOnObject](D:/md_files/NSFNoteOLEGetAssociateFileOnObject.md)
---
