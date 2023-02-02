##### Function : Dir
##### DirCollectionNthEntry - Find the Nth entry in the hCollection collection.
---
##### #include <dircoll.h>
DIRENTRY LNPUBLIC **DirCollectionNthEntry(**

	DIRCOLLECTION  hCollection,
	DWORD  N);
**Description :**
Find the Nth entry in the hCollection collection.
**Parameters :**
Input :
hCollection  -  Handle to the collection of entries to be navigated.

N  -  The n-th

Output :
(routine)  -  A reference to the N-th match in hCollection. This does not use or update the collection's internally maintained "current" directory entry cursor. If the input hCollection is NULLDIRCOLLECTION, or N is out of bounds, or the Nth entry has already been freed, then the return value is NULLDIRENTRY. 
DirEntryFree() may be called on the returned directory entry object to remove it from the collection. Or, the entry will be freed when DirCollectionFree() is called. 


**See Also :**
[DirCollectionFirstEntry](D:/md_files/DirCollectionFirstEntry.md)
[DirCollectionFree](D:/md_files/DirCollectionFree.md)
[DirCollectionGetNumEntries](D:/md_files/DirCollectionGetNumEntries.md)
[DirCollectionNextEntry](D:/md_files/DirCollectionNextEntry.md)
---
