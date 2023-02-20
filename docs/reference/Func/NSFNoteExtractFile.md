##### Function : File Attachment
##### NSFNoteExtractFile - Extract a file from an item in a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteExtractFile(

	NOTEHANDLE  note_handle,
	BLOCKID  item_blockid,
	const char far *file_name,
	ENCRYPTION_KEY far *DecryptionKey);
```
**Description :**

Creates a disk file from the contents of an attached item (referenced by its 
BLOCKID).  The BLOCKID can be easily obtained by item name using NSFItemInfo.  
The file_name parameter specifies the path, file name, and extension of the 
file to be created.  If only a file name and extension are supplied, the file 
will be created in the current working directory.

   Note: NSFNoteExtractFile should be deprecated from Notes/Domino 8.0.1. The 
preferred function to use in their place is NSFNoteCipherDecrypt.

**Parameters :**
Input :
note_handle  -  Handle of note from which disk file will be extracted.

item_blockid  -  BLOCKID of the attachment item from which file is to be extracted.

file_name  -  A null-terminated file name of the file that will be created.  File names are accepted in LMBCS;  names are translated to the character set used by the operating system when the new output file is created.

DecryptionKey  -  Use NULL if the attachment is not encrypted.  Otherwise, use a pointer to the ENCRYPTION_KEY structure returned by NSFNoteDecrypt.

Output :
(routine)  -  Return status from this call includes:

NOERROR - Successfully extracted file.

ERR_ENCODING - Unknown type of compression technique.

ERR_NOEXTRACT_ENCRYPTED - You must supply the decryption key in order to extract this file.

ERR_NOTE_BADATTSIGN - Attachment has been modified or corrupted since signed!

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[NSFNoteAttachFile](/reference/Func/NSFNoteAttachFile)
[NSFNoteDecrypt](/reference/Func/NSFNoteDecrypt)
[NSFNoteDetachFile](/reference/Func/NSFNoteDetachFile)
[NSFNoteExtractFileExt](/reference/Func/NSFNoteExtractFileExt)
---
