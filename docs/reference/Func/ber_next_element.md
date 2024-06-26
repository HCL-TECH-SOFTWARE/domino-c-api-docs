##### Function : Basic Encoding Rules
##### ber_next_element - Used to traverse a set or sequence of data values.
---
```
#include <lber.h>
ber_tag_t LNPUBLIC ber_next_element(

	BerElement *ber,
	ber_len_t *len,
	char *last);
```
**Description :**

This routine is used, along with ber_first_element(), to traverse a set or 
sequence of data values. 

The ber_first_element() function is used to return the tag of the first element 
of a set or sequence of data values. It also returns the last byte of a set or 
sequence of data values. This "last" parameter should be passed to subsequent 
calls to ber_next_element(), which returns similar information, namely the tag 
of the next element to be parsed and the last element in a set or sequence of 
data values.

Implemented as a macro:

#define ber_next_element(ber, len, last) ND_ber_next_element((ber), (len), 
(last))

**Parameters :**
Input :
ber  -  This state pointer points at the start of the next element to be parsed. 

len  -  The length of the element to be parsed.

Output :
(routine)  -  Returns the tag of the next element to be parsed. LBER_DEFAULT is returned if there are no further values.


last  -  The last element in a set or sequence of data values.


**See Also :**
[BerElement](/domino-c-api-docs/reference/Data/BerElement)
[ber_first_element](/domino-c-api-docs/reference/Func/ber_first_element)
[ber_len_t](/domino-c-api-docs/reference/Data/ber_len_t)
[ber_tag_t](/domino-c-api-docs/reference/Data/ber_tag_t)
---
