##### Function : Basic Encoding Rules
##### ber_flatten - Allocates a berval struct.
---
```
#include <lber.h>
int LNPUBLIC ber_flatten(

	BerElement *ber,
	struct berval **bvPtr);
```
**Description :**

This routine allocates a berval struct whose contents are a BER encoding taken 
from the ber argument. The bvPtr pointer points to the returned berval 
structure, which should be freed using ber_bvfree().

The use of ber_flatten on a BerElement in which all '{' and '}' format 
modifiers have not been properly matched is an error (i.e., -1 will be returned 
by ber_flatten() if this situation is exists).

Implemented as a macro:

#define ber_flatten(ber, bvPtr) ND_ber_flatten((ber), (bvPtr))

**Parameters :**
Input :
ber  -  Pointer to a BerElement structure which is encoded and stored as the contents of the berval struct returned by this routine.

Output :
(routine)  -  0 on success and -1 on error.


bvPtr  -  Pointer to a pointer to the returned berval structure.


**See Also :**
[BerElement](/domino-c-api-docs/reference/Data/BerElement)
[Berval](/domino-c-api-docs/reference/Data/Berval)
---
