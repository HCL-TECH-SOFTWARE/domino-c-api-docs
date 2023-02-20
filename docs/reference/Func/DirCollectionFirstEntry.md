##### Function : Dir
##### DirCollectionFirstEntry - Find the first entry in the hCollection collection. 
---
```
#include <dircoll.h>
DIRENTRY LNPUBLIC DirCollectionFirstEntry(

	DIRCOLLECTION  hCollection);
```
**Description :**

This function sets the "current" entry to the first entry and then retrieves it.
  Warning:This function is not re-entrant! Always use the 
DirCollectionNthEntry() function if the collection is shared amongst processes 
or threads!

**Parameters :**
Input :
hCollection  -  Handle to the collection of entries to be navigated.

Output :
(routine)  -  A reference to the first entry in hCollection. This sets the collection's internally maintained "current" directory entry cursor. If the input hCollection is NULLDIRCOLLECTION then the return value is NULLDIRENTRY. 
DirEntryFree() may be called on the returned directory entry object to remove it from the collection. Or, the entry will be freed when DirCollectionFree() is called. 



**See Also :**
[DirCollectionGetNumEntries](/reference/Func/DirCollectionGetNumEntries)
[DirCollectionNextEntry](/reference/Func/DirCollectionNextEntry)
---
