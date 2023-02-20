##### Function : Note
##### NSFNoteCopyAndEncrypt - Copies and encrypts (seals) a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteCopyAndEncrypt(

	NOTEHANDLE  hSrcNote,
	WORD  EncryptFlags,
	NOTEHANDLE far *rethDstNote);
```
**Description :**

This function copies and encrypts (seals) the encryption enabled fields in a 
note (including the note's file objects). 

NSFNoteCopyAndEncrypt can encrypt a note in several ways -- by using the Domino 
public key of the caller, by using specified secret encryption keys stored in 
the caller's ID, or by using the Domino public keys of specified users, if the 
note does not have any mime parts.

NSFNoteCopyAndEncrypt decides which type of encryption to do based upon the 
setting of the flag passed to it in its EncryptFlags argument.  If the 
ENCRYPT_WITH_USER_PUBLIC_KEY flag is set, it uses the caller's public ID to 
encrypt the note.  In this case, only the user who encodes the note can decrypt 
it.  This feature allows an individual to protect information from anyone else.

If, instead, the ENCRYPT_WITH_USER_PUBLIC_KEY flag is not set, then the 
function expects the note to contain  a field named ITEM_NAME_NOTE_SEALNAMES ( 
defined to be "SecretEncryptionKeys" in stdnames.h), a field named 
ITEM_NAME_NOTE_SEALUSERS  (defined to be "PublicEncryptionKeys" in stdnames.h), 
or both.  Each field is either a TYPE_TEXT or TYPE_TEXT_LIST field.

ITEM_NAME_NOTE_SEALNAMES contains the name(s) of the secret encryption keys in 
the calling user's ID to be used to encrypt the note.  This feature is intended 
to allow a group to encrypt some of the notes in a single database in a way 
that only they can decrypt them -- they must share the secret encryption keys 
among themselves first for this to work.

ITEM_NAME_NOTE_SEALUSERS contains the name(s) of  users, in canonical format.  
The note will be encrypted with each user's Domino public key.  The user can 
then decrypt the note with the private key in the user's ID.  This feature 
provides a way to encrypt documents, such as mail documents, for another user.

The note must contain at least one encryption enabled item (an item with the 
ITEM_SEAL flag set) in order to be encrypted.  Use NSFNoteClose to close the 
note handle and deallocate the memory associated with it.

If the note has mime parts and flag ENCRYPT_SMIME_IF_MIME_PRESENT is set, then 
it is SMIME encrypted.

If the document is to be signed as well as encrypted, you must sign the 
document (NSFNoteSign or NSFNoteSignExt) before using NSFNoteCopyAndEncrypt.

**Parameters :**
Input :
hSrcNote  -  Handle to the open note.

EncryptFlags  -  Optional.  Use 0 for the note to be encrypted with a personal key.  An ITEM_NAME_NOTE_SEALNAMES item containing the name of the personal key must have been appended to the note prevously.  See ENCRYPT_xxx for other options.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully copied and encrypted.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


rethDstNote  -  Pointer to the handle of the returned copy of the note.  This returned copy is the encrypted version of the note.


**See Also :**
[NSFNoteDecrypt](/reference/Func/NSFNoteDecrypt)
[ENCRYPT_xxx](/reference/Symb/ENCRYPT_xxx)
---
