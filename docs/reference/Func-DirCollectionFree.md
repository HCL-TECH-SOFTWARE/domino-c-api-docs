##### Function : Dir
##### DirCollectionFree - Free the memory associated with a collection of entries returned by a search operation.
---
##### #include <dircoll.h>
void LNPUBLIC **DirCollectionFree(**

	DIRCOLLECTION  hCollection);
**Description :**
This function calls DirEntryFree(),deallocating each of the directory entries 
in this collection.
**Parameters :**
Input :
hCollection  -  Handle to the collection of entries to free. If NULLDIRCOLLECTION then nothing is freed.

Output :
(routine)  -  This function returns a VOID,if the free fails a NULLDIRCOLLECTION is returned in the parameter.


**See Also :**
[DIRCOLLECTION](D:/md_files/DIRCOLLECTION.md)
[DirCollectionFirstEntry](D:/md_files/DirCollectionFirstEntry.md)
[DirCollectionGetNumEntries](D:/md_files/DirCollectionGetNumEntries.md)
[DirCollectionNextEntry](D:/md_files/DirCollectionNextEntry.md)
[DirCollectionNthEntry](D:/md_files/DirCollectionNthEntry.md)
[DirCollectionPrint](D:/md_files/DirCollectionPrint.md)
---
