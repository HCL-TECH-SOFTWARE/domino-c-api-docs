##### Function : Basic Encoding Rules
##### ber_scanf - Used to decode a BerElement
---
##### #include <lber.h>
ber_tag_t LNVARARGS **ber_scanf(**

	BerElement *ber,
	const char *fmt,
	<Any 'C' type>  optional_var1, ...);
**Description :**
The ber_scanf() function is used to decode a BER element in much the same way 
that scanf() works. One important difference, though, is that some state 
information is kept with the ber argument so that multiple calls can be made to 
ber_scanf() to sequentially read from the BER element. It reads from ber, a 
pointer to a BerElement, interprets the bytes according to the format string 
fmt, and stores the results in its additional arguments. The format string 
contains conversion specifications which are used to direct the interpretation 
of the BER element. The format string can contain the following characters. 

'a'     Octet string.  
A char ** argument must be supplied.  Memory is allocated, filled with the 
contents of the octet string, zero-terminated, and the pointer to the string is 
stored in the argument.  The returned value should be freed using ldap_memfree. 
The tag of the element must indicate the primitive form (constructed strings 
are not supported) but is otherwise ignored and discarded during the decoding.  
This format cannot be used with octet strings which could contain null bytes.

'O'     Octet string.  
A struct berval ** argument must be supplied, which upon return points to an 
allocated struct berval containing the octet string and its length.  
ber_bvfree() SHOULD be called to free the allocated memory.  The tag of the 
element must indicate the primitive form (constructed strings are not 
supported) but is otherwise ignored during the decoding.

'b'     Boolean.  
A pointer to a ber_int_t must be supplied. The ber_int_t value stored will be 0 
for FALSE or nonzero for TRUE. The tag of the element must indicate the 
primitive form but is otherwise ignored during the decoding.

'e'     Enumerated.  
A pointer to a ber_int_t must be supplied. The enumerated value stored will be 
in host byte order.  The tag of the element must indicate the primitive form 
but is otherwise ignored during the decoding.  ber_scanf() will return an error 
if the value of the enumerated value cannot be stored in a ber_int_t.

'i'     Integer.  
A pointer to a ber_int_t must be supplied. The ber_int_t value stored will be 
in host byte order.  The tag of the element must indicate the primitive form 
but is otherwise ignored during the decoding.  ber_scanf() will return an error 
if the integer cannot be stored in a ber_int_t.

'B'     Bitstring.  
A char ** argument must be supplied which will point to the allocated bits, 
followed by a ber_len_t * argument, which will point to the length (in bits) of 
the bitstring returned. ldap_memfree should be called to free the bitstring.  
The tag of the element must indicate the primitive form (constructed bit-
strings are not supported) but is otherwise ignored during the decoding.

'n'     Null.  
No argument is needed.  The element is verified to have a zero-length value and 
is skipped.  The tag is ignored.

't'     Tag.  
A pointer to a ber_tag_t must be supplied.  The ber_tag_t value stored will be 
the tag of the next element in the BerElement ber, represented so it can be 
written using the 't' format of ber_printf().  The decoding position within the 
ber argument is unchanged by this; that is, the fact that the tag has been 
retrieved does not affect future use of ber.

'v'     Several octet strings.  
A char *** argument must be supplied, which upon return points to an allocated 
NULL-terminated array of char *'s containing the octet strings.  NULL is stored 
if the sequence is empty.  ldap_memfree should be called to free each element 
of the array and the array itself.  The tag of the sequence and of the octet 
strings are ignored.

'V'     Several octet strings (which could contain null bytes).  
A struct berval *** must be supplied, which upon return points to a allocated 
NULL-terminated array of struct berval *'s containing the octet strings and 
their lengths.  NULL is stored if the sequence is empty. ber_bvecfree() can be 
called to free the allocated memory.  The tag of the sequence and of the octet 
strings are ignored.

'x'     Skip element.  
The next element is skipped.  No argument is needed.

'{'     Begin sequence.  
No argument is needed.  The initial sequence tag and length are skipped.

'}'     End sequence.  
No argument is needed.

'['     Begin set.  
No argument is needed.  The initial set tag and length are skipped.

']'     End set.  
No argument is needed.


Implemented as a macro:

#define ber_scanf ND_ber_scanf
**Parameters :**
Input :
ber  -  A pointer to a BerElement returned by ber_init().

fmt  -  Routine interprets the bytes according to this format string.

Output :
(routine)  -  A ber_tag_t  structure.

Routine returns LBER_ERROR on error, and a different value on success.  If an error occurred, the values of all the result parameters are undefined.


optional_var1, ...  -  Routine stores its results in these optional arguments.

**See Also :**
[Berval](D:/md_files/Berval.md)
[ber_bvecfree](D:/md_files/ber_bvecfree.md)
[ber_bvfree](D:/md_files/ber_bvfree.md)
[ber_int_t](D:/md_files/ber_int_t.md)
[ber_len_t](D:/md_files/ber_len_t.md)
[ber_printf](D:/md_files/ber_printf.md)
[ber_tag_t](D:/md_files/ber_tag_t.md)
[ldap_memfree](D:/md_files/ldap_memfree.md)
---
