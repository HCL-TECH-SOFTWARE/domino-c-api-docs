##### Function : Note
##### NSFNoteCheck - Checks that each item in a note is correctly structured.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteCheck(**

	DHANDLE  note_handle);
**Description :**
This function examines each item (field) in the note and determines if the 
items are correctly formed. In general, the checking involves verifying that 
the length of each item matches its data type. For multi-value items, the 
function checks that the overall field length is correct for the number of 
elements in the list.

This function will not catch every error that can exist within a note.
**Parameters :**
Input :
note_handle  -  The handle of the note that you want to test.

Output :
(routine)  -  Returns NOERROR if the note appears to be correctly structured.  The return codes include:

ERR_INVALID_ITEMLEN if an item's overall length does not match its data type.

ERR_INVALID_ITEMTYPE if an item's type is not recognized.

ERR_xxx  which is a STATUS code returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


**See Also :**
[](D:/md_files/.md)
---
