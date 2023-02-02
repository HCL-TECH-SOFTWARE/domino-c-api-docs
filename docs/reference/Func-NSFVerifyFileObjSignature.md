##### Function : Note
##### NSFVerifyFileObjSignature - Verifies a signature on an object.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFVerifyFileObjSignature(**

	DBHANDLE  hDB,
	BLOCKID  bhItem);
**Description :**
This function verifies a signature on an object such as a file attachment.  It 
returns an error if the signature did not verify.
**Parameters :**
Input :
hDB  -  Handle to the opened database.

bhItem  -  BLOCKID of the object.

Output :
(routine)  -   Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The object signature was successfully verified or the object was not signed.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


**See Also :**
[NSFNoteVerifySignature](D:/md_files/NSFNoteVerifySignature.md)
---
