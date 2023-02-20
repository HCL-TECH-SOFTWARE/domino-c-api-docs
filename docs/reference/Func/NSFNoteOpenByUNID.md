##### Function : Note
##### NSFNoteOpenByUNID - Opens a note, given the note's Universal Note ID.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteOpenByUNID(

	DBHANDLE  hDB,
	UNID far *pUNID,
	WORD  flags,
	NOTEHANDLE far *rethNote);
```
**Description :**

This function takes the Universal Note ID and reads the note into memory and 
returns a handle to the in-memory copy. This function only supports the set of 
16-bit WORD options described in the entry OPEN_xxx.

Use NSFNoteClose to close the note handle and deallocate the memory associated 
with it.

**Parameters :**
Input :
hDB  -  The handle of the open database that contains the note.

pUNID  -  The Universal Note ID.

flags  -   Flags that control the manner in which the note is opened. This, in turn, controls what information about the note is available to you and how it is structured. The flags are defined in OPEN_xxx (note) and may be or'ed together to combine functionality.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully opened the note.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



rethNote  -  The address in which the handle of the opened note is returned.


**See Also :**
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
[OPEN_xxx (note)](/reference/Symb/OPEN_xxx (note))
---
