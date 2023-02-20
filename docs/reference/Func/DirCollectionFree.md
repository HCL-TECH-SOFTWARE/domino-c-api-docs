##### Function : Dir
##### DirCollectionFree - Free the memory associated with a collection of entries returned by a search operation.
---
```
#include <dircoll.h>
void LNPUBLIC DirCollectionFree(

	DIRCOLLECTION  hCollection);
```
**Description :**

This function calls DirEntryFree(),deallocating each of the directory entries 
in this collection.

**Parameters :**
Input :
hCollection  -  Handle to the collection of entries to free. If NULLDIRCOLLECTION then nothing is freed.

Output :
(routine)  -  This function returns a VOID,if the free fails a NULLDIRCOLLECTION is returned in the parameter.



**See Also :**
[DIRCOLLECTION](/reference/Data/DIRCOLLECTION)
[DirCollectionFirstEntry](/reference/Func/DirCollectionFirstEntry)
[DirCollectionGetNumEntries](/reference/Func/DirCollectionGetNumEntries)
[DirCollectionNextEntry](/reference/Func/DirCollectionNextEntry)
[DirCollectionNthEntry](/reference/Func/DirCollectionNthEntry)
[DirCollectionPrint](/reference/Func/DirCollectionPrint)
---
