##### Function : Database
##### DirCollectionNextEntry - Find the next entry after the "current" entry in the hCollection collection. 
---
```
#include <dircoll.h>
DIRENTRY LNPUBLIC DirCollectionNextEntry(

	DIRCOLLECTION  hCollection);
```
**Description :**

Find the next entry after the "current" entry in the hCollection collection. 
Warning: 
This function is not re-entrant! Always use the DirCollectionNthEntry() 
function if the collection is shared amongst processes or threads!

**Parameters :**
Input :
hCollection  -  Handle to the collection of entries to be navigated.

Output :
(routine)  -  A reference to the next match in hCollection. This uses and updates the collection's internally maintained "current" directory entry cursor. If there are no more entries in the collection then NULLDIRENTRY will be returned. If the input hCollection is NULLDIRCOLLECTION then the return value is NULLDIRENTRY. 
DirEntryFree() may be called on the returned directory entry object to remove it from the collection. Or, the entry will be freed when DirCollectionFree() is called. 



**See Also :**
[DirCollectionFirstEntry](/reference/Func/DirCollectionFirstEntry)
[DirCollectionFree](/reference/Func/DirCollectionFree)
[DirCollectionGetNumEntries](/reference/Func/DirCollectionGetNumEntries)
[DirCollectionNthEntry](/reference/Func/DirCollectionNthEntry)
---
