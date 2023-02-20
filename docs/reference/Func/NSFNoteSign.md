##### Function : Note
##### NSFNoteSign - Appends a digital signature to a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteSign(

	NOTEHANDLE  hNote);
```
**Description :**

This function signs a document by creating a unique electronic signature and 
appending this signature to the note.   A signature constitutes proof of the 
user's identity and serves to assure the reader that the user was the real 
author of the document. 

The signature is derived from the User ID. A signature item has data type 
TYPE_SIGNATURE and item flags ITEM_SEAL. The data value of the signature item 
is a digest of the data stored in items in the note, signed with the user's 
private key. 

NSFNoteSign signs entire document. It creates a digest of all the items in the 
note, and appends a signature item with field name $Signature 
(ITEM_NAME_NOTE_SIGNATURE).  Use NSFNoteSignExt() to sign a section of a note.

If the document to be signed is encrypted, this function will attempt to 
decrypt the document in order to generate a valid signature.  If you want the 
document to be signed and encrypted, you must sign the document  before using 
NSFNoteCopyAndEncrypt.

Note:  When the Notes user interface opens a note, it always uses the 
OPEN_EXPAND option to promote items of type number to number list, and items of 
type text to text list.  In order for a signature created or verified through 
this API call to work correctly with the Notes user interface, the OPEN_EXPAND 
option must be used when the note is opened.

**Parameters :**
Input :
hNote  -  The handle of an open note.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully signed.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.



**See Also :**
[NSFNoteSignExt](/reference/Func/NSFNoteSignExt)
[NSFNoteUnsign](/reference/Func/NSFNoteUnsign)
[NSFNoteVerifySignature](/reference/Func/NSFNoteVerifySignature)
[OPEN_xxx (note)](/reference/Symb/OPEN_xxx (note))
---
