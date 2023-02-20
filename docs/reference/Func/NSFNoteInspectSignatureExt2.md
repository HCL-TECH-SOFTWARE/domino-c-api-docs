##### Function : Security
##### NSFNoteInspectSignatureExt2 - Verify the signature on a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteInspectSignatureExt2(

	NOTEHANDLE  hNote,
	KFHANDLE  hKFC,
	char far *pzSigItemName,
	TIMEDATE far *retWhenSigned,
	char far *retSigner,
	char far *retCertifier,
	WORD *retItemCount,
	DHANDLE *rethItemIDs,
	DWORD  Reserved,
	void *pReserved);
```
**Description :**

This routine will verify the signature on a note, returning: when, by whom and 
the name of the certifier.

**Parameters :**
Input :
hNote  -  Open handle to a note.

hKFC  -  Handle to an ID file.  Pass NULL for current user's ID.

pzSigItemName  -  Name of the field on the note that contains the signature. May be NULL.

Reserved  -  Reserved, should be set to 0.

pReserved  -  Reserved, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully signed.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


retWhenSigned  -  Time and date when the note was signed.

retSigner  -  Name of the signer.

retCertifier  -  Name of the certifier.

retItemCount  -  Number of items signed.  May be NULL.

rethItemIDs  -  An array containing the BlockIDs of the items signed.  May be NULL.


**See Also :**
[SECKFMOpen](/reference/Func/SECKFMOpen)
---
