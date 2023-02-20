##### Function : Basic Encoding Rules
##### ber_bvdup - Creates a new copy of a berval structure based on the original.
---
```
#include <lber.h>
struct berval * LNPUBLIC ber_bvdup(

	const struct berval *bv);
```
**Description :**

This function creates a new copy of a berval structure based on the one 
supplied in bv. The bv_val field in the returned berval structure points to a 
different area of memory than the bv_val field in the bv argument.  The NULL 
pointer is returned on error (e.g. out of memory).

Implemented as a macro:

#define ber_bvdup(bv) ND_ber_bvdup((bv))

**Parameters :**
Input :
bv  -   Pointer to the original berval structure.

Output :
(routine)  -   Pointer to the new berval structure.



**See Also :**
[Berval](/reference/Data/Berval)
---
