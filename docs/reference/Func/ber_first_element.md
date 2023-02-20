##### Function : Basic Encoding Rules
##### ber_first_element - Used to traverse a set or sequence of data values.
---
```
#include <lber.h>
ber_tag_t LNPUBLIC ber_first_element(

	BerElement *ber,
	ber_len_t *len,
	char **last);
```
**Description :**

This routine is used, along with ber_next_element(), to traverse a set or 
sequence of data values. 

The ber_first_element() function is used to return the tag of the first element 
of a set or sequence of data values. It also returns the last byte of a set or 
sequence of data values. This "last" parameter should be passed to subsequent 
calls to ber_next_element(), which returns similar information, namely the tag 
of the next element to be parsed and the last element in a set or sequence of 
data values.

The len and last values should not be used by applications other than as 
arguments to ber_next_element().

Implemented as a macro:

#define ber_first_element(ber, len, last) ND_ber_first_element((ber), (len), 
(last))

**Parameters :**
Input :
ber  -  This state pointer points at the start of the first element to be parsed in the set or sequence of data values.  

len  -  The length of the element to be parsed.

Output :
(routine)  -  Returns the tag of the first element to be parsed. LBER_DEFAULT is returned if the set or sequence of data values is empty.


last  -  The last byte of a set or sequence of data values.


**See Also :**
[BerElement](/reference/Data/BerElement)
[ber_len_t](/reference/Data/ber_len_t)
[ber_next_element](/reference/Func/ber_next_element)
[ber_tag_t](/reference/Data/ber_tag_t)
---
