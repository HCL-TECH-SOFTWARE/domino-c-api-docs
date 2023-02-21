##### Function : Views
##### COLLECTIONPOSITIONSIZE - Computes space used by a COLLECTIONPOSITION.
---
```
#include <nif.h>
int COLLECTIONPOSITIONSIZE(

	COLLECTIONPOSITION *collpos);
```
**Description :**

A macro used to compute the size of the portion of a COLLECTIONPOSITION 
structure that is actually used.  This is only necessary when collection 
positions are packed into a buffer in less space than using the 
COLLECTIONPOSITION structure (e.g. NIFReadEntries).

#define COLLECTIONPOSITIONSIZE(p) (sizeof(DWORD) * ((p)->Level+2))

**Parameters :**
Input :
collpos  -  Pointer to a COLLECTIONPOSITION.  Note : The Level and Tumbler array values for the COLLECTIONPOSITION must have been previously assigned.

Output :
(routine)  -  Returns size of the COLLECTIONPOSITION structure in bytes.



**See Also :**
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
