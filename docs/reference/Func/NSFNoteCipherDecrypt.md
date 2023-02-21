##### Function : encryption
##### NSFNoteCipherDecrypt - Decrypts (unseals) a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteCipherDecrypt(

	NOTEHANDLE  hNote,
	KFHANDLE  hKFC,
	DWORD  DecryptFlags,
	CIPHERHANDLE far *rethCipherForAttachments,
	DWORD  Reserved,
	void *pReserved);
```
**Description :**

This function decrypts an encrypted note, using the appropriate encryption key 
stored in the user's ID file.  If the user does not have the appropriate 
encryption key to decrypt the note, an error is returned.  

	This function supports new cryptographic keys and algorithms introduced 
in Release 8.0.1 as well as any from releases prior to 8.0.1.  Thus it is 
preferred over the functions NSFNoteDecrypt and NSFNoteDecryptExt2 in cases 
where their ENCRYPTION_KEY argument is specified and is used in subsequent 
operations.

By default, file attachments and objects are not decrypted, but a flag may be 
specified to do so as part of this function (see below).  Alternatively, this 
function can optionally return a CIPHERHANDLE which can then be used as input 
to other functions to decrypt attachments or objects.


**Parameters :**
Input :
hNote  -  Handle to the open note.

hKFC  -  Handle to an ID file.  Pass NULLKFHANDLE for current user's ID.

DecryptFlags  -  Use DECRYPT_ATTACHMENTS_IN_PLACE to decrypt attachments as part of this operation, or if this note is to be encrypted again with NSFNoteCopyAndEncrypt.  See DECRYPT_xxx.  Otherwise use 0.

rethCipherForAttachments  -  If non-NULL on input, the referenced CIPHERHANDLE is assumed to be an existing handle obtained from a previous call, and it is freed with NSFCipherDestroy before overwriting with new data; otherwise, the CIPHERHANDLE must be equal to NULLCIPHERHANDLE on input.

Reserved  -  Reserved, must be 0.

pReserved  -  Reserved, must be NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully decrypted.
ERR_NOTE_NOT_SEALED - The note is not encrypted.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


rethCipherForAttachments  -  Optional.  Pointer to a returned CIPHERHANDLE.  The CIPHERHANDLE may then be passed in to NSFNoteCipherExtractFile or NSFNoteCipherExtractWithCallback to decrypt a file attachment.  Use NULL if this information is not needed.  When done with the CIPHERHANDLE, your code must call NSFCipherDestroy to release memory and resources associated with it.  The returned CIPHERHANDLE will always be equal to NULLCIPHERHANDLE if the function returns any error status other than NOERROR.


**Sample Usage :**
```
NOTEID note1_id, note2_id;
STATUS error = NOERROR;
CIPHERHANDLE rethCipherAttachments;
error = NSFNoteCreate(hDb, &hnote1);
error = NSFNoteCopyAndEncrypt(hnote1, ENCRYPT_WITH_USER_PUBLIC_KEY, &hnote2);

error = OSMemoryAllocate(0, MAXONESEGSIZE, &rethCipherAttachments);
error = NSFNoteCipherDecrypt(hnote2, NULLKFHANDLE, 0, &rethCipherAttachments, 
0, NULL);
```
**See Also :**
[NSFNoteCipherExtractFile](/domino-c-api-docs/reference/Func/NSFNoteCipherExtractFile)
[NSFNoteCopyAndEncrypt](/domino-c-api-docs/reference/Func/NSFNoteCopyAndEncrypt)
---
