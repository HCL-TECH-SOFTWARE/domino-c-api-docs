##### Function : Basic Encoding Rules
##### ber_peek_tag - Returns the tag of the next element to be parsed.
---
##### #include <lber.h>
ber_tag_t LNPUBLIC **ber_peek_tag(**

	BerElement *ber,
	ber_len_t *len);
**Description :**
This routine returns the tag of the next element to be parsed.  The decoding 
position within the ber argument is unchanged by this call; that is, the fact 
that ber_peek_tag() has been called does not affect future use of ber.


Implemented as a macro:

#define ber_peek_tag(ber, len) ND_ber_peek_tag((ber), (len))
**Parameters :**
Input :
ber  -  This state pointer points at the tag of the next element to be parsed.

len  -  The length of the element to be parsed.

Output :
(routine)  -  The tag of the next element to be parsed.

LBER_DEFAULT is returned if there is no further data to be read.  


**See Also :**
[BerElement](D:/md_files/BerElement.md)
[ber_len_t](D:/md_files/ber_len_t.md)
[ber_tag_t](D:/md_files/ber_tag_t.md)
---
