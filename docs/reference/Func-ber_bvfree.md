##### Function : Basic Encoding Rules
##### ber_bvfree - Frees a berval structure from memory.
---
##### #include <lber.h>
void LNPUBLIC **ber_bvfree(**

	struct berval *bv);
**Description :**
This routine frees a berval structure from memory.

Implemented as a macro:

#define ber_bvfree(bv)  ND_ber_bvfree((bv))
**Parameters :**
Input :
bv  -  Pointer to the berval structure that you want to free from memory.

Output :
(routine)  -  None.


**See Also :**
[Berval](D:/md_files/Berval.md)
---
