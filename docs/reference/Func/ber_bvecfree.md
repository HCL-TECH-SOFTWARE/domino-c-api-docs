##### Function : Basic Encoding Rules
##### ber_bvecfree - Frees an array of berval structures.
---
```
#include <lber.h>
void LNPUBLIC ber_bvecfree(

	struct berval **bv);
```
**Description :**

Frees an array of berval structures. Each of the berval structures in the array 
are freed using ber_bvfree(), then the array itself is freed.

Implemented as a macro:

#define ber_bvecfree(bv) ND_ber_bvecfree((bv))

**Parameters :**
Input :
bv  -  A pointer to a pointer to an array of berval structures.

Output :
(routine)  -  None.



**See Also :**
[Berval](/reference/Data/Berval)
[ber_bvfree](/reference/Func/ber_bvfree)
---
