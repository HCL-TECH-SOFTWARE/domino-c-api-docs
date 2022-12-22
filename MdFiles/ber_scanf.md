




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 6**



**Function : Basic Encoding Rules;
LDAP**



**ber\_scanf** **- Used to
decode a BerElement**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



ber\_tag\_t
LNVARARGS **ber\_scanf(**  

      BerElement \*ber,  

      const char \*fmt,  

      <Any 'C' type>  optional\_var1, ...**);**



**Description :**



The ber\_scanf()
function is used to decode a BER element in much the same way that scanf()
works. One important difference, though, is that some state information is kept
with the ber argument so that multiple calls can be made to ber\_scanf() to
sequentially read from the BER element. It reads from ber, a pointer to a
BerElement, interprets the bytes according to the format string fmt, and stores
the results in its additional arguments. The format string contains conversion
specifications which are used to direct the interpretation of the BER element.
The format string can contain the following characters. 


 


'a'    
Octet string.  


A char \*\*
argument must be supplied.  Memory is allocated, filled with the contents of
the octet string, zero-terminated, and the pointer to the string is stored in
the argument.  The returned value should be freed using ldap\_memfree. The tag
of the element must indicate the primitive form (constructed strings are not
supported) but is otherwise ignored and discarded during the decoding.  This
format cannot be used with octet strings which could contain null bytes.  

  

'O'     Octet string.  


A struct
berval \*\* argument must be supplied, which upon return points to an allocated
struct berval containing the octet string and its length.  ber\_bvfree() SHOULD
be called to free the allocated memory.  The tag of the element must indicate
the primitive form (constructed strings are not supported) but is otherwise
ignored during the decoding.  

  

'b'     Boolean.  


A pointer to
a ber\_int\_t must be supplied. The ber\_int\_t value stored will be 0 for FALSE or
nonzero for TRUE. The tag of the element must indicate the primitive form but
is otherwise ignored during the decoding.  

  

'e'     Enumerated.  


A pointer to
a ber\_int\_t must be supplied. The enumerated value stored will be in host byte
order.  The tag of the element must indicate the primitive form but is
otherwise ignored during the decoding.  ber\_scanf() will return an error if the
value of the enumerated value cannot be stored in a ber\_int\_t.  

  

'i'     Integer.  


A pointer to
a ber\_int\_t must be supplied. The ber\_int\_t value stored will be in host byte
order.  The tag of the element must indicate the primitive form but is
otherwise ignored during the decoding.  ber\_scanf() will return an error if the
integer cannot be stored in a ber\_int\_t.  

  

'B'     Bitstring.  


A char \*\*
argument must be supplied which will point to the allocated bits, followed by a
ber\_len\_t \* argument, which will point to the length (in bits) of the bitstring
returned. ldap\_memfree should be called to free the bitstring.  The tag of the
element must indicate the primitive form (constructed bit-  

strings are not supported) but is otherwise ignored during the decoding.  

  

'n'     Null.  


No argument
is needed.  The element is verified to have a zero-length value and is
skipped.  The tag is ignored.  

  

't'     Tag.  


A pointer to
a ber\_tag\_t must be supplied.  The ber\_tag\_t value stored will be the tag of
the next element in the BerElement ber, represented so it can be written using
the 't' format of ber\_printf().  The decoding position within the ber argument
is unchanged by this; that is, the fact that the tag has been retrieved does
not affect future use of ber.  

  

'v'     Several octet strings.  


A char \*\*\*
argument must be supplied, which upon return points to an allocated
NULL-terminated array of char \*'s containing the octet strings.  NULL is stored
if the sequence is empty.  ldap\_memfree should be called to free each element
of the array and the array itself.  The tag of the sequence and of the octet
strings are ignored.  

  

'V'     Several octet strings (which could contain null bytes).  


A struct
berval \*\*\* must be supplied, which upon return points to a allocated
NULL-terminated array of struct berval \*'s containing the octet strings and
their lengths.  NULL is stored if the sequence is empty. ber\_bvecfree() can be
called to free the allocated memory.  The tag of the sequence and of the octet
strings are ignored.  

  

'x'     Skip element.  


The next
element is skipped.  No argument is needed.  

  

'{'     Begin sequence.  


No argument
is needed.  The initial sequence tag and length are skipped.  

  

'}'     End sequence.  


No argument
is needed.  

  

'['     Begin set.  


No argument
is needed.  The initial set tag and length are skipped.  

  

']'     End set.  


No argument
is needed.


 


 


Implemented
as a macro:


 


#define
ber\_scanf   ND\_ber\_scanf


 


**Parameters :**



Input :  

ber  -  A pointer to a BerElement returned by ber\_init().  

  

fmt  -  Routine interprets the bytes according to this format string.  

  




Output :  

(routine)  -  A ber\_tag\_t  structure.  

  

Routine returns LBER\_ERROR on error, and a different value on success.  If an error
occurred, the values of all the result parameters are undefined.  

  

  

optional\_var1, ...  -  Routine stores its results in these optional arguments.  

  




 **See Also :**


**[Berval](Berval.md)**


**[ber\_bvecfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/74460D83CB094A9C85256F5C00486F09)**


**[ber\_bvfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6E60A0A308298A3985256F5C00486F08)**


**[ber\_int\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CE802B4A671FCEE385256ACB0067102F)**


**[ber\_len\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5E4AA411D51AEE8685256ACB0066FB61)**


**[ber\_printf](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BE804184555D6E2C85256F5C00486F0B)**


**[ber\_tag\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/55264E307F9D5DE285256ACB0066B45C)**


**[ldap\_memfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F11748459A77A7EE85256F5C00488A7A)**



----------------------------------------------------------------------------------------------------------


 





