##### Function : Note
##### NSFNoteUnsign - Unsigns a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteUnsign(

	NOTEHANDLE  hNote);
```
**Description :**

This function removes the ITEM_NAME_NOTE_SIGNATURE item from a note.

**Parameters :**
Input :
hNote  -  The handle of an open note.

Output :
(routine)  -    Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully unsigned.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.



**See Also :**
[NSFNoteSign](/reference/Func/NSFNoteSign)
---
