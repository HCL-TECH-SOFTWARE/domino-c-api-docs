##### Function : Note
##### NSFNoteDecrypt - Decrypts (unseals) a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteDecrypt(

	HANDLE  hNote,
	WORD  DecryptFlags,
	ENCRYPTION_KEY far *retKeyForAttachments);
```
**Description :**

This function decrypts an encrypted note, using the appropriate encryption key 
stored in the user's ID file.  If the user does not have the appropriate 
encryption key to decrypt the note, an error is returned.  

File attachments are not decrypted.  However, this function can optionally 
return an ENCRYPTION_KEY structure pointer which can then be used in 
NSFNoteExtractFile or NSFNoteExtractFileExt to decrypt a file attachment.

    Note: NSFNoteDecrypt should be deprecated from Notes/Domino 8.0.1. The 
preferred function to use in their place is NSFNoteCipherDecrypt.

**Parameters :**
Input :
hNote  -  Handle to the open note.

DecryptFlags  -  Use DECRYPT_ATTACHMENTS_IN_PLACE if this note is to be encrypted again with NSFNoteCopyAndEncrypt.  Otherwise use 0.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully decrypted.
ERR_NOTE_NOT_SEALED - The note is not encrypted.
ERR_BSAFE_UNSUPPORTED_CRYPTO_OP - One possible cause of this error is when the note is encrypted using an encryption key type that is supported only in N/D 8.01 and later (e.g. AES).  The function cannot write the retKeyForAttachments output parameter in such cases because an ENCRYPTION_KEY data structure is not sufficient to describe that key type.  A work-around is to continue to use this function but specify the DECRYPT_ATTACHMENTS_IN_PLACE flag; this means any attachments will be decrypted immediately, and thus the retKeyForAttachments argument should be unnecessary.  The recommended action is to modify the code to use NSFNoteCipherDecrypt instead, which supports all key types.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.



retKeyForAttachments  -  Optional.  Pointer to a returned ENCRYPTION_KEY structure.  This pointer may then be passed in to NSFNoteExtractFile or NSFNoteExtractFileExt to decrypt a file attachment.  Use NULL if this information is not needed.


**See Also :**
[NSFNoteCopyAndEncrypt](/domino-c-api-docs/reference/Func/NSFNoteCopyAndEncrypt)
[NSFNoteExtractFile](/domino-c-api-docs/reference/Func/NSFNoteExtractFile)
[NSFNoteExtractFileExt](/domino-c-api-docs/reference/Func/NSFNoteExtractFileExt)
---
