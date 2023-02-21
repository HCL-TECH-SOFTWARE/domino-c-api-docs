##### Function : Basic Encoding Rules
##### ber_skip_tag - Returns the tag of the next element to be parsed.
---
```
#include <lber.h>
ber_tag_t LNPUBLIC ber_skip_tag(

	BerElement *ber,
	ber_len_t *len);
```
**Description :**

This routine returns the tag of the next element to be parsed. It is similar to 
ber_peek_tag(), except that the state pointer in the ber argument is advanced 
past the first tag and length, and is pointed to the value part of the next 
element.  This routine should only be used with constructed types and 
situations when a BER encoding is used as the value of an OCTET STRING. 

Implemented as a macro:

#define ber_skip_tag(ber, len) ND_ber_skip_tag((ber), (len))

**Parameters :**
Input :
ber  -  This state pointer points at the value of the next element to be parsed.

len  -  The length of the element to be parsed.

Output :
(routine)  -  The tag of the next element to be parsed.



**See Also :**
[BerElement](/domino-c-api-docs/reference/Data/BerElement)
[ber_peek_tag](/domino-c-api-docs/reference/Func/ber_peek_tag)
[ber_tag_t](/domino-c-api-docs/reference/Data/ber_tag_t)
---
