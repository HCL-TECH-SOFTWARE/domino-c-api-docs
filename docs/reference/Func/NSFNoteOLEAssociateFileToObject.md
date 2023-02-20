##### Function : OLE
##### NSFNoteOLEAssociateFileToObject - Associate an attachment ($FILE) with an OLE object.
---
```
#include <nsfasc.h>
STATUS LNPUBLIC NSFNoteOLEAssociateFileToObject(

	NOTEHANDLE  hNote,
	char *pszObjName,
	char *pszFileSpec,
	char *pszAttachmentName,
	WORD  wIfExists,
	DWORD  dwFlags,
	DWORD *pdwId);
```
**Description :**

The association can be made using an existing associated $FILE or can create a 
new $FILE from a system file and then create the association.  If there is no 
file spec, but there is an attachment name and the attachment exists, use 
existing attachment for association.

**Parameters :**
Input :
hNote  -  Handle of the OLE object's note.

pszObjName  -  Pointer to name of the OLE object in the note.

pszFileSpec  -  Pointer to the file specification of the file to associate with the object (see NSFNoteAttachFile - file_name for details).  If attachment already exists, set this to NULL.

pszAttachmentName  -  Pointer to the name of the attachment to associate.

wIfExists  -  see ASSOCITEM_IFEXISTS_xxx

dwFlags  -  Currently not used.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_ARGS_INVALID - A required argument (hNote, pszObjName, pszAttachmentName) was not supplied.

ERR_ASSOCITEM_ATTACHMENT - A required argument (pszFileSpec) was not supplied.

ERR_ASSOCITEM_ATTACHMENT_ITEM_EXISTS - File attachment already exists.

ERR_xxx - STATUS returned from a lower level Notes function call.  Use OSLoadString and display/log the error.


pdwId  -  Pointer to the location which contains the Id of the associated $FILE.


**See Also :**
[ASSOCITEM_IFEXISTS_xxx](/reference/Symb/ASSOCITEM_IFEXISTS_xxx)
[NSFNoteAttachFile](/reference/Func/NSFNoteAttachFile)
[NSFNoteOLEDisassociateFileFromObject](/reference/Func/NSFNoteOLEDisassociateFileFromObject)
[NSFNoteOLEGetAssociateFileOnObject](/reference/Func/NSFNoteOLEGetAssociateFileOnObject)
---
