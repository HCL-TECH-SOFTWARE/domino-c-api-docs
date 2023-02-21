##### Function : Basic Encoding Rules
##### ber_printf - Used to encode a BerElement
---
```
#include <lber.h>
int LNVARARGS ber_printf(

	BerElement *ber,
	const char *fmt,
	<Any 'C' type>  optional_var1, ...);
```
**Description :**

This routine is used to encode a BerElement in much the same way that sprintf() 
works.  One important difference, though, is that state information is kept in 
the ber argument so that multiple calls can be made to ber_printf() to append 
to the end of the BER element. Ber_printf() writes to ber, a pointer to a 
BerElement. It interprets and formats its arguments according to the format 
string fmt. As with sprintf(), each character in fmt refers to an argument to 
ber_printf().The format string can contain the following characters: 

't'     Tag.  
The next argument is a ber_tag_t specifying the tag to override the next 
element to be written to the ber.  This works across calls.  The integer tag 
value should contain the tag class, constructed bit, and tag value.  For 
example, a tag of "[3]" for a constructed type is 0xA3U.  All implementations 
MUST support tags that fit in a single octet (i.e., where the tag value is less 
than 32) and they MAY support larger tags.

'b'     Boolean.  
The next argument is an ber_int_t, containing either 0 for FALSE or 0xff for 
TRUE.  A boolean element is output.  If this format character is not preceded 
by the 't' format modifier, the tag 0x01U is used for the element.

'e'     Enumerated.  
The next argument is a ber_int_t, containing the enumerated value in the host's 
byte order.  An enumerated element is output.  If this format character is not 
preceded by the 't' format modifier, the tag 0x0AU is used for the element.

'i'     Integer.  
The next argument is a ber_int_t, containing the integer in the host's byte 
order.  An integer element is output. If this format character is not preceded 
by the 't' format modifier, the tag 0x02U is used for the element.

'B'     Bitstring.  
The next two arguments are a char * pointer to the start of the bitstring, 
followed by a ber_len_t containing the number of bits in the bitstring.  A 
bitstring element is output, in primitive form.  If this format character is 
not preceded by the 't' format modifier, the tag 0x03U is used for the element.

'X'     Reserved and not to be used.

'n'     Null.  
No argument is needed.  An ASN.1 NULL element is output. If this format 
character is not preceded by the 't' format modifier, the tag 0x05U is used for 
the element.

'o'     Octet string.  
The next two arguments are a char *, followed by a ber_len_t with the length of 
the string.  The string may contain null bytes and are do not have to be 
zero-terminated.   An octet string element is output, in primitive form.  If 
this format character is not preceded by the 't' format modifier, the tag 0x04U 
is used for the element.

's'     Octet string.  
The next argument is a char * pointing to a zero-terminated string.  An octet 
string element in primitive form is output, which does not include the trailing 
'\0' (null) byte. If this format character is not preceded by the 't' format 
modifier, the tag 0x04U is used for the element.

'v'     Several octet strings.  
The next argument is a char **, an array of char * pointers to zero-terminated 
strings.  The last element in the array must be a NULL pointer. The octet 
strings do not include the trailing '\0' (null) byte.  Note that a construct 
like '{v}' is used to get an actual sequence of octet strings. The 't' format 
modifier cannot be used with this format character.

'V'     Several octet strings.  
A NULL-terminated array of struct berval *'s is supplied.  Note that a 
construct like '{V}' is used to get an actual sequence of octet strings. The 
't' format modifier cannot be used with this format character.

'{'     Begin sequence.  
No argument is needed.  If this format character is not preceded by the 't' 
format modifier, the tag 0x30U is used.

'}'     End sequence.  
No argument is needed.  The 't' format modifier cannot be used with this format 
character.

'['     Begin set.  
No argument is needed.  If this format character is not preceded by the 't' 
format modifier, the tag 0x31U is used.

']'     End set.  
No argument is needed.  The 't' format modifier cannot be used with this format 
character.

Each use of a '{' format character should be matched by a '}' character, either 
later in the format string, or in the format string of a subsequent call to 
ber_printf() for that BerElement.  The same applies to the '[' and ']' format 
characters.

Sequences and sets nest, and implementations of this API must maintain internal 
state to be able to properly calculate the lengths.

Implemented as a macro:

#define ber_printf ND_ber_printf

**Parameters :**
Input :
ber  -  Must be a pointer to a BerElement returned by ber_alloc_t(). 

fmt  -  Routine interprets and formats its arguments according to this format string.

optional_var1, ...  -  Optional argument.

Output :
(routine)  -  -1 if there is an error during encoding and a non-negative number if successful.  



**See Also :**
[ber_alloc_t](/domino-c-api-docs/reference/Func/ber_alloc_t)
[ber_int_t](/domino-c-api-docs/reference/Data/ber_int_t)
[ber_len_t](/domino-c-api-docs/reference/Data/ber_len_t)
[ber_printf](/domino-c-api-docs/reference/Func/ber_printf)
[ber_tag_t](/domino-c-api-docs/reference/Data/ber_tag_t)
---
