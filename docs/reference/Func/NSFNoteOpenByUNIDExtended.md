##### Function : Note
##### NSFNoteOpenByUNIDExtended - Return a Notes document handle using the Universal Note ID.
---
```
#include <nsfnote.h>
STATUS NSFNoteOpenByUNIDExtended(

	DBHANDLE  hDB,
	UNID  pUNID,
	DWORD  flags,
	NOTEHANDLE  rethNote);
```
**Description :**

Read the Universal Note ID into memory and return a handle to the in-memory 
copy. DWORD options are described in the entry OPEN_xxx. 

Use NSFNoteClose to close the note handle and deallocate the memory associated 
with it.

**Parameters :**
Input :
hDB  -  The handle of the open database that contains the note.

pUNID  -  The Universal Note ID.

flags  -  Flags that control the manner in which the note is opened. This, in turn, controls what information about the note is available to you and how it is structured. The flags are defined in OPEN_xxx (note) and may be or'ed together to combine functionality.

Output :
(routine)  -  Returns status from the call, either success or an error.


rethNote  -  The address in which the handle of the opened note is returned.


**Sample Usage :**
```
	NOTEHANDLE hNote = NULLHANDLE;
  DWORD Flags = OPEN_CANONICAL | OPEN_UNLINKED | OPEN_RAW_MIME;

  /* Where myUNID is a variable of type UNID. */
	if(status = NSFNoteOpenByUNIDExtended(hDb, myUNID, Flags, &hNote))
	 printf("UNID not found or Note is invalid, error = %e", status);
```
**See Also :**
---
