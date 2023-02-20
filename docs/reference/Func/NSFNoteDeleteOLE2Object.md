##### Function : OLE
##### NSFNoteDeleteOLE2Object - Delete an OLE2 structured storage object.
---
```
#include <nsfole.h>
STATUS LNPUBLIC NSFNoteDeleteOLE2Object(

	NOTEHANDLE  hNote,
	char *pszObjectName,
	BOOL  fDeleteObjInfo,
	ENCRYPTION_KEY *pEncryptionKey,
	DWORD  dwFlags);
```
**Description :**

Delete an OLE2 structured storage object stored in a note as an extendable file 
object.  Also, optionally delete the associated $OLEOBJINFO item.

**Parameters :**
Input :
hNote  -  Note handle of open note

pszObjectName  -  Name of the OLE $FILE object which is the "master" extendable file object ("ext***") in the set of $FILE objects that comprise this OLE object.

fDeleteObjInfo  -  True if the associated $OLEOBJINFO with this object should also be deleted.

pEncryptionKey  -  The note's bulk data encryption key, acquired from NSFNoteDecrypt(...). Necessary to decrypt the $FILE extent table.

dwFlags  -  Additional flags, unused at this time, must be 0.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_NSF_NOT_SUPPORTED - This function is not supported on this platform.  In Release 5.0 through 5.0.7 of Domino and Notes, this function was supported on Windows 32-bit platforms only.  As of Release 5.0.8, this function is supported on all Domino and Notes platforms.

ERR_xxx - STATUS returned from a lower level Notes function call.  Use OSLoadString and display/log the error.



**See Also :**
[NSFNoteAttachOLE2Object](/reference/Func/NSFNoteAttachOLE2Object)
[NSFNoteExtractOLE2Object](/reference/Func/NSFNoteExtractOLE2Object)
---
