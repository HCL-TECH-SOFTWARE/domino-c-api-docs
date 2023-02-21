##### Function : Basic Encoding Rules
##### ber_alloc_t - Constructs and returns a BerElement structure.
---
```
#include <lber.h>
BerElement * LNPUBLIC ber_alloc_t(

	int  options);
```
**Description :**

This routine constructs and returns a BerElement structure.  The NULLBER 
pointer is returned on error.  The options field contains a bitwise-or of 
options which are to be used when generating the encoding of this BerElement. 
Unrecognized option bits are ignored.

The BerElement returned by ber_alloc_t() is initially empty.  Calls to 
ber_printf() will append bytes to the end of the ber_alloc_t().

Implemented as a macro:

#define ber_alloc_t(options)  ND_ber_alloc_t((options))

**Parameters :**
Input :
options  -  A bitwise-or of options which are to be used when generating the encoding of this BerElement.

Output :
(routine)  -  Pointer to a BerElement structure.



**See Also :**
[BerElement](/domino-c-api-docs/reference/Data/BerElement)
[NULLBER](/domino-c-api-docs/reference/Symb/NULLBER)
---
