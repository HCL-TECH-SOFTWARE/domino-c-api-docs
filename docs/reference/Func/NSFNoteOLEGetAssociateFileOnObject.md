##### Function : OLE
##### NSFNoteOLEGetAssociateFileOnObject - Get a specified associated attachment ($FILE) on an OLE object.
---
```
#include <nsfasc.h>
STATUS LNPUBLIC NSFNoteOLEGetAssociateFileOnObject(

	NOTEHANDLE  hNote,
	char *pszObjName,
	DHANDLE far *ppszAttachmentName,
	DWORD  dwId);
```
**Description :**

The name returned is in OSMemAlloc'd memory.  It is the caller's responsibility 
to free this memory.

**Parameters :**
Input :
hNote  -  Handle of the OLE object's note.

pszObjName  -  Pointer to the name of the OLE object.

dwId  -  Id of the attachment to get.  Ids start at zero.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_ARGS_INVALID - A required argument (hNote, pszObjName, phszAttachmentName) was not supplied.

ERR_ASSOCITEM_NOITEMS - There are no files associated with the OLE object.

ERR_ITEM_NOT_FOUND - Attachment (dwId) not found.

ERR_xxx - STATUS returned from a lower level Notes function call.  Use OSLoadString and display/log the error.


ppszAttachmentName  -  Pointer to the location where the handle to the name of the attachment is placed upon return.


**See Also :**
---
