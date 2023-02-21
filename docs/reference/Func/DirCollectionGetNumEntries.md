##### Function : Dir
##### DirCollectionGetNumEntries - Returns the number of entries in the hCollection collection. 
---
```
#include <dircoll.h>
DWORD LNPUBLIC DirCollectionGetNumEntries(

	const DIRCOLLECTION  hCollection);
```
**Description :**

This function returns the number of entries in the hCollection collection,if 
hCollection is NULLDIRCOLLECTION, 0 is returned. 

**Parameters :**
Input :
hCollection  -  Handle to the collection of entries.

Output :
(routine)  -  Number of entries in the collection. If hCollection is NULLDIRCOLLECTION, 0 is returned. 



**See Also :**
[DirCollectionFirstEntry](/domino-c-api-docs/reference/Func/DirCollectionFirstEntry)
[DirCollectionNextEntry](/domino-c-api-docs/reference/Func/DirCollectionNextEntry)
[DirCollectionNthEntry](/domino-c-api-docs/reference/Func/DirCollectionNthEntry)
---
