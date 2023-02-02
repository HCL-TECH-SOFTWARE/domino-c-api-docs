##### Function : Rich Text
##### NSFComputeObjectDigest - Create an object containing a signature digest.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFComputeObjectDigest(**

	DHANDLE  hNote,
	BLOCKID  bItem);
**Description :**
This function will create a $FILE object containing a signature digest. that 
can be appended when a file is attached to a note.
**Parameters :**
Input :
hNote  -  Handle to an open note.

bItem  -  Block ID of a $FILE item.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The object was successfully created.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


**See Also :**
[](D:/md_files/.md)
---
