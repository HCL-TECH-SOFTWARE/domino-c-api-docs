##### Function : Database
##### NSFDbCreateObjectStore - Create a Note Object store.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCreateObjectStore(

	const char far *PathName,
	BOOL  ForceCreation);
```
**Description :**

A Note Object Store allows maintaining a single copy of large notes (for 
example, a note with large amounts of attached data).  Entries in standard 
Domino databases can be linked to a note in a Note Object Store.  This function 
is used to create the Note Object Store.

The notes in a Note Object Store are accessed using the NSF routines - for 
example, NSFDbOpen() (or NSFDbOpenExtended()), NSFNoteOpen(), etc.

**Parameters :**
Input :
PathName  -  Null-terminated file name for the Note Object Store.

ForceCreation  -  If TRUE and the Note Object Store already exists, a new, empty store will replace the existing store.

Output :
(routine)  -  (routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR
ERR_EXISTS
ERR_DBCLASS



**See Also :**
[NSFDbGetObjectStoreID](/reference/Func/NSFDbGetObjectStoreID)
[NSFDbSetObjectStoreID](/reference/Func/NSFDbSetObjectStoreID)
---
