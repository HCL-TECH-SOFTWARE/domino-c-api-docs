##### Function : Note
##### NSFNoteIsSignedOrSealed - Determines if note is signed and/or sealed.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFNoteIsSignedOrSealed(

	NOTEHANDLE  note_handle,
	BOOL far *signed_flag_ptr,
	BOOL far *sealed_flag_ptr);
```
**Description :**

This function determines if an in-memory note is signed and/or sealed 
(encrypted).  

A signed Note contains an additional item, which is generated using the Note 
Author's private encryption key from his or her USER ID.  This does not prevent 
you from accessing any of the note's Items or header information, except of 
course, the ITEM_NAME_NOTE_SIGNATURE item itself. 

A sealed Note contains at least two additional items,  ITEM_NAME_NOTE_SEAL and 
ITEM_NAME_NOTE_SEALDATA.  You may use NSFNoteDecrypt to decrypt a sealed note.

This functions works for both notes and native MIME messages.  However, only 
the outer envelope of the native MIME message is checked.  This means that 
SMIME signed/sealed messages which are nested within the native MIME message 
will not be detected.

**Parameters :**
Input :
note_handle  -  The handle of an open note.

Output :
(routine)  -  Returned from this call-

TRUE - Note was either signed or sealed.
FALSE - Note was neither signed nor sealed.


signed_flag_ptr  -  The addres of a BOOL in which the Signed state of the Note is returned.  TRUE if Signed and False if not Signed.

sealed_flag_ptr  -  The address of a BOOL in which the Sealed state of the Note is returned.  TRUE if Sealed and False if not Sealed.


**See Also :**
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteDecrypt](/domino-c-api-docs/reference/Func/NSFNoteDecrypt)
---
