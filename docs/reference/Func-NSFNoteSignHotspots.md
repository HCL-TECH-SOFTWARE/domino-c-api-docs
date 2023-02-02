##### Function : Note
##### NSFNoteSignHotspots - Sign the source and object code associated with the hotspots on a document.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteSignHotspots(**

	NOTEHANDLE  hNote,
	DWORD  dwFlags,
	BOOL *retfSigned);
**Description :**
This function will sign all hotspots in a document that contain object code.  
Using the current ID, signature data will be added to any signature containing 
CD records for hotspots having code within TYPE_COMPOSITE items. 

This routine only operates on documents.  If the note is a design element, the 
routine returns NOERROR without signing anything.
**Parameters :**
Input :
hNote  -  The handle of an open note.

dwFlags  -  Reserved for future use.  Should be set to ZERO.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The hotspots were successfully signed.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


retfSigned  -  TRUE if any hotspots are signed, otherwise FALSE.  Set to NULL if this information is not needed.

**See Also :**
[NSFHotSpotSign](D:/md_files/NSFHotSpotSign.md)
---
