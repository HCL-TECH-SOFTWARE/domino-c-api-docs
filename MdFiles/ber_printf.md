




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



**ber\_printf** **- Used to
encode a BerElement**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



int
LNVARARGS **ber\_printf(**  

      BerElement \*ber,  

      const char \*fmt,  

      <Any 'C' type>  optional\_var1, ...**);**



**Description :**



This routine
is used to encode a BerElement in much the same way that sprintf() works.  One
important difference, though, is that state information is kept in the ber
argument so that multiple calls can be made to ber\_printf() to append to the
end of the BER element. Ber\_printf() writes to ber, a pointer to a BerElement.
It interprets and formats its arguments according to the format string fmt. As
with sprintf(), each character in fmt refers to an argument to ber\_printf().The
format string can contain the following characters: 


  

't'     Tag.  


The next
argument is a ber\_tag\_t specifying the tag to override the next element to be
written to the ber.  This works across calls.  The integer tag value should
contain the tag class, constructed bit, and tag value.  For example, a tag of
"[3]" for a constructed type is 0xA3U.  All implementations MUST
support tags that fit in a single octet (i.e., where the tag value is less than
32) and they MAY support larger tags.  

  

'b'     Boolean.  


The next
argument is an ber\_int\_t, containing either 0 for FALSE or 0xff for TRUE.  A
boolean element is output.  If this format character is not preceded by the 't'
format modifier, the tag 0x01U is used for the element.  

  

'e'     Enumerated.  


The next
argument is a ber\_int\_t, containing the enumerated value in the host's byte
order.  An enumerated element is output.  If this format character is not
preceded by the 't' format modifier, the tag 0x0AU is used for the element.  

  

'i'     Integer.  


The next
argument is a ber\_int\_t, containing the integer in the host's byte order.  An
integer element is output. If this format character is not preceded by the 't'
format modifier, the tag 0x02U is used for the element.  

  

'B'     Bitstring.  


The next two
arguments are a char \* pointer to the start of the bitstring, followed by a ber\_len\_t
containing the number of bits in the bitstring.  A bitstring element is output,
in primitive form.  If this format character is not preceded by the 't' format
modifier, the tag 0x03U is used for the element.  

  

'X'     Reserved and not to be used.  

  

'n'     Null.  


No argument
is needed.  An ASN.1 NULL element is output. If this format character is not
preceded by the 't' format modifier, the tag 0x05U is used for the element.  

  

'o'     Octet string.  


The next two
arguments are a char \*, followed by a ber\_len\_t with the length of the string. 
The string may contain null bytes and are do not have to be zero-terminated.  
An octet string element is output, in primitive form.  If this format character
is not preceded by the 't' format modifier, the tag 0x04U is used for the
element.  

  

's'     Octet string.  


The next
argument is a char \* pointing to a zero-terminated string.  An octet string
element in primitive form is output, which does not include the trailing '\0'
(null) byte. If this format character is not preceded by the 't' format
modifier, the tag 0x04U is used for the element.  

  

'v'     Several octet strings.  


The next
argument is a char \*\*, an array of char \* pointers to zero-terminated strings. 
The last element in the array must be a NULL pointer. The octet strings do not
include the trailing '\0' (null) byte.  Note that a construct like '{v}' is
used to get an actual sequence of octet strings. The 't' format modifier cannot
be used with this format character.  

  

'V'     Several octet strings.  


A NULL-terminated
array of struct berval \*'s is supplied.  Note that a construct like '{V}' is
used to get an actual sequence of octet strings. The 't' format modifier cannot
be used with this format character.  

  

'{'     Begin sequence.  


No argument
is needed.  If this format character is not preceded by the 't' format
modifier, the tag 0x30U is used.  

  

'}'     End sequence.  


No argument
is needed.  The 't' format modifier cannot be used with this format character.  

  

'['     Begin set.  


No argument
is needed.  If this format character is not preceded by the 't' format
modifier, the tag 0x31U is used.  

  

']'     End set.  


No argument
is needed.  The 't' format modifier cannot be used with this format character.  

  

Each use of a '{' format character should be matched by a '}' character, either
later in the format string, or in the format string of a subsequent call to
ber\_printf() for that BerElement.  The same applies to the '[' and ']' format
characters.  

  

Sequences and sets nest, and implementations of this API must maintain internal
state to be able to properly calculate the lengths.


 


Implemented
as a macro:


 


#define
ber\_printf    ND\_ber\_printf


 


**Parameters :**



Input :  

ber  -  Must be a pointer to a BerElement returned by ber\_alloc\_t().   

  

fmt  -  Routine interprets and formats its arguments according to this format
string.  

  

optional\_var1, ...  -  Optional argument.  

  




Output :  

(routine)  -  -1 if there is an error during encoding and a non-negative number
if successful.    

  

  




 **See Also :**


**[ber\_alloc\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3CBFE85E4F1A206785256F5C00486F0D)**


**[ber\_int\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CE802B4A671FCEE385256ACB0067102F)**


**[ber\_len\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5E4AA411D51AEE8685256ACB0066FB61)**


**[ber\_printf](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BE804184555D6E2C85256F5C00486F0B)**


**[ber\_tag\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/55264E307F9D5DE285256ACB0066B45C)**



----------------------------------------------------------------------------------------------------------


 





