##### Function : Views
##### COLLECTIONPOSITIONSIZE16 - Computes space used by a COLLECTIONPOSITION16.
---
```
#include <nif.h>
int COLLECTIONPOSITIONSIZE16(

	COLLECTIONPOSITION16 *collpos);
```
**Description :**

A macro used to compute the size of the portion of a COLLECTIONPOSITION16 
structure that is actually used.  This is only necessary when collection 
positions are packed into a buffer in less space than using the 
COLLECTIONPOSITION16 structure (e.g. NIFReadEntries).

#define COLLECTIONPOSITIONSIZE16(p) (sizeof(DWORD) * ((p)->Level+2))

**Parameters :**
Input :
collpos  -  Pointer to a COLLECTIONPOSITION16.  Note : The Level and Tumbler array values for the COLLECTIONPOSITION16 must have been previously assigned.

Output :
(routine)  -  Returns size of the COLLECTIONPOSITION16 structure in bytes.



**See Also :**
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
