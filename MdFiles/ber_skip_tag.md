




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



**ber\_skip\_tag** **- Returns
the tag of the next element to be parsed.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



ber\_tag\_t
LNPUBLIC **ber\_skip\_tag(**  

      BerElement \*ber,  

      ber\_len\_t \*len**);**



**Description :**



This routine
returns the tag of the next element to be parsed. It is similar to
ber\_peek\_tag(), except that the state pointer in the ber argument is advanced
past the first tag and length, and is pointed to the value part of the next
element.  This routine should only be used with constructed types and
situations when a BER encoding is used as the value of an OCTET STRING. 


 


Implemented
as a macro:


 


#define
ber\_skip\_tag(ber, len)          ND\_ber\_skip\_tag((ber), (len))


 


**Parameters :**



Input :  

ber  -  This state pointer points at the value of the next element to be
parsed.  

  

len  -  The length of the element to be parsed.  

  




Output :  

(routine)  -  The tag of the next element to be parsed.  

  

  




 **See Also :**


**[BerElement](BerElement.md)**


**[ber\_peek\_tag](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7A1456F1E585F43A85256F5C00486F04)**


**[ber\_tag\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/55264E307F9D5DE285256ACB0066B45C)**



----------------------------------------------------------------------------------------------------------


 





