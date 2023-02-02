##### Function : Note
##### NSFNoteVerifySignature - Verifies a signature on a note.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteVerifySignature(**

	NOTEHANDLE  hNote,
	char far *SignatureItemName,
	TIMEDATE far *retWhenSigned,
	char far *retSigner,
	char far *retCertifier);
**Description :**
This function verifies a signature on a note or section(s) within a note.  It 
returns an error if a signature did not verify.  All of the output arguments 
for this function are optional.

Note:  When the Notes user interface opens a note, it always uses the 
OPEN_EXPAND option to promote items of type number to number list, and items of 
type text to text list.  In order for a signature created or verified through 
this API call to work correctly with the Notes user interface, the OPEN_EXPAND 
option must be used when the note is opened.
**Parameters :**
Input :
hNote  -  The handle of an open note.

SignatureItemName  -  Specify NULL to verify the signature of a note.  Specify the SignatureItemName to verify a signature of a field that resides in a section of a note.  The SignatureItemName is a zero-terminated LMBCS string of the form $Sig_<sectionname>,  where <sectionname> is the name of a section to verify.

Output :
(routine)  -   Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note or section signature was successfully verified.
ERR_NOTE_NOT_SIGNED - The note or section has no signature. 
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


retWhenSigned  -  Optional.  Pointer to returned TIMEDATE structure containing the time of the signature.  Use NULL if this information is not needed.

retSigner  -  Optional.  Pointer to the returned user name of the one who signed the note or section.  The caller should allocate a buffer size of MAXUSERNAME.  Use NULL if this information is not needed.

retCertifier  -  Optional.  Pointer to the returned common certifier.  The caller should allocate a buffer size of MAXUSERNAME.  Use NULL if this information is not needed.

**See Also :**
[NSFNoteSign](D:/md_files/NSFNoteSign.md)
[NSFNoteSignExt](D:/md_files/NSFNoteSignExt.md)
---
