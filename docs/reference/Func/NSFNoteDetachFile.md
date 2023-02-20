##### Function : File Attachment
##### NSFNoteDetachFile - Deletes an attached file from a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteDetachFile(

	NOTEHANDLE  note_handle,
	BLOCKID  item_blockid);
```
**Description :**

Deletes an attached file item (referenced by its BLOCKID) from a note and also 
deallocates the disk space used to store the attached file in the database.  
The BLOCKID of the item can be easily obtained by item name from a call to 
NSFItemInfo.

**Parameters :**
Input :
note_handle  -  Handle of the Note which contains the attached file.

item_blockid  -  BLOCKID of the attachment item that is to be detached/deleted.

Output :
(routine)  -  Return status from this call.  Always returns NOERROR.



**See Also :**
[NSFItemInfo](/reference/Func/NSFItemInfo)
[NSFNoteAttachFile](/reference/Func/NSFNoteAttachFile)
[NSFNoteExtractFile](/reference/Func/NSFNoteExtractFile)
---
