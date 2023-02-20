##### Function : Security
##### NSFNoteSignExt3 - Sign all or specific items in a note and append a signature item to the note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteSignExt3(

	NOTEHANDLE  hNote,
	KFHANDLE  hKFC,
	const char far *SignatureItemName,
	WORD  ItemCount,
	DHANDLE  hItemIDs,
	DWORD  Flags,
	DWORD  Reserved,
	void *pReserved);
```
**Description :**

This function works just like NSFNoteSignExt - it allows you to sign just the 
fields that reside in a section of a document, and to give the signature item 
the appropriate name.  In addition, this function allows you to pass a flag to 
determine how MIME parts will be signed.  This function requires  you to 
specify a handle to a specific ID file.

NSFNoteSignExt3 generates a signature item with the specified name and appends 
this signature item to the note. A signature item has data type TYPE_SIGNATURE 
and item flags ITEM_SEAL. The data value of the signature item is a digest of 
the data stored in items in the note, signed with the user's private key.

To sign all the fields that reside in one section of a note, you need the name 
of the section and the BLOCKIDs of all the items in the section. Format a 
signature item name as a zero-terminated ASCI string of the form 
$Sig_<sectionname>.  Allocate a block of memory in which to store an array of 
item BLOCKIDs.  Initialize this array with the BLOCKIDs of all the items in the 
section.  Then call NSFNoteSignExt3 specifying the handle to the note, the 
signature item name, the count of items in the section, and the handle to the 
block of memory containing the array of item BLOCKIDs.  NSFNoteSignExt3 will  
create a digital signature from the specified items and append this digital 
signature item to the note.

 If the note has MIME parts then it will be SMIME signed.  If not, or the Flags 
parameter is set to allow Notes signature on MIME parts, then it will be Notes 
signed.

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
hNote  -  Handle to an open note that is to be signed.

hKFC  -  Handle to an ID file.  Pass NULL for current user's ID.

SignatureItemName  -  A zero-terminated LMBCS string specifying the name of the signature item to append. Specify NULL to append a signature item with the name $Signature (ITEM_NAME_NOTE_SIGNATURE). To sign a section, specify a name with the format $Sig_<sectionname>, where <sectionname> is the name of a section to sign.


ItemCount  -  The number of BLOCKIDs in the array specified by hItemIDs. Specify MAXWORD to sign all the signable items in the note.

hItemIDs  -  Handle to memory block containing an array of item BLOCKIDs. To sign a section, the array must contain the item BLOCKIDs of all items in the section. To sign the entire document, specify NULLHANDLE .

Flags  -   If 0, and the note has MIME parts, then it will be SMIME signed.  If not or the Flags parameter is set to allow Notes signature on MIME parts then it will be Notes signed.  See SIGN_NOTES_IF_MIME_PRESENT.

Reserved  -  Reserved, should be 0.

pReserved  -  Reserved, should be NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully signed.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.



**See Also :**
[SECKFMOpen](/reference/Func/SECKFMOpen)
[SIGN_NOTES_IF_MIME_PRESENT](/reference/Symb/SIGN_NOTES_IF_MIME_PRESENT)
---
