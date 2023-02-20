##### Function : Views
##### NIFLocateNote - Update collection position for a note.
---
```
#include <nif.h>
STATUS LNPUBLIC NIFLocateNote(

	HCOLLECTION  hCollection,
	COLLECTIONPOSITION far *IndexPos,
	NOTEID  NoteID);
```
**Description :**

When a collection is modified (for example, when another user adds or deletes a 
document), the collection position for a note may no longer be valid.  
NIFLocateNote will locate the specified note ID in the collection, and update 
the collection position to the new position.

**Parameters :**
Input :
hCollection  -  Handle to the collection.

IndexPos  -  Pointer to the old collection position.

NoteID  -  Note ID of the note to locate.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


IndexPos  -  Collection position updated to match the position in the modified collection.


**See Also :**
[NIFUpdateCollection](/reference/Func/NIFUpdateCollection)
---
