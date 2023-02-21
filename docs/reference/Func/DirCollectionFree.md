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
[DIRCOLLECTION](/domino-c-api-docs/reference/Data/DIRCOLLECTION)
[DirCollectionFirstEntry](/domino-c-api-docs/reference/Func/DirCollectionFirstEntry)
[DirCollectionGetNumEntries](/domino-c-api-docs/reference/Func/DirCollectionGetNumEntries)
[DirCollectionNextEntry](/domino-c-api-docs/reference/Func/DirCollectionNextEntry)
[DirCollectionNthEntry](/domino-c-api-docs/reference/Func/DirCollectionNthEntry)
[DirCollectionPrint](/domino-c-api-docs/reference/Func/DirCollectionPrint)
---
