##### Function : Basic Encoding Rules
##### ber_init - Constructs a BerElement structure.
---
```
#include <lber.h>
BerElement * LNPUBLIC ber_init(

	const struct berval *bv);
```
**Description :**

This function constructs a BerElement structure and returns a new BerElement 
containing a copy of the data in the bv argument.  

Implemented as a macro:

#define ber_init(bv)  ND_ber_init((bv))

**Parameters :**
Input :
bv  -  Pointer to a berval structure, a copy of which is stored in the BerElement struct returned by this routine.

Output :
(routine)  -  Pointer to a BerElement structure. This routine returns the NULL pointer on error.



**See Also :**
[BerElement](/reference/Data/BerElement)
[Berval](/reference/Data/Berval)
---
