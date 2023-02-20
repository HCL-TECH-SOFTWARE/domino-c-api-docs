##### Function : Database
##### NSFDbCreateNoteID - Allocate a Note ID.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCreateNoteID(

	DBHANDLE  hDB,
	BOOL  fData,
	NOTEID *retNoteID);
```
**Description :**

This function ensures that the returned Note ID is unique to the database.  A 
likely use for this routine is by an Extension Manager DLL to create a unique 
ID for an object in an external database.  

This function works for a local databases only.

**Parameters :**
Input :
hDB  -  Database handle.

fData  -  TRUE if the Note ID to be allocated is for the note class DATA.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is.


retNoteID  -  Pointer at which the new Note ID is returned.


**See Also :**
---
