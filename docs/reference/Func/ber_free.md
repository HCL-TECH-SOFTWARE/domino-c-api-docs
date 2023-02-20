##### Function : Basic Encoding Rules
##### ber_free - Frees a BerElement.
---
```
#include <lber.h>
void LNPUBLIC ber_free(

	BerElement *ber,
	int  freebuf);
```
**Description :**

Frees a BerElement which is returned from the API calls ber_alloc_t() or 
ber_init().  Each BerElement should be freed by the caller.

Implemented as a macro:

#define ber_free(ber, freebuf)  ND_ber_free((ber), (freebuf))

**Parameters :**
Input :
ber  -  Pointer to a BerElement structure.

freebuf  -  BER functions always set this parameter to 1 to ensure that the internal buffer used by the BER functions is freed as well as the BerElement container itself. (Note: LDAP functions set this parameter to 0).

Output :
(routine)  -  None.



**Sample Usage :**
```
ber_free(ber, 0);

```
**See Also :**
[BerElement](/reference/Data/BerElement)
[ber_alloc_t](/reference/Func/ber_alloc_t)
[ber_init](/reference/Func/ber_init)
---
