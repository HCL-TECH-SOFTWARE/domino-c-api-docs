




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



**ber\_first\_element** **- Used to
traverse a set or sequence of data values.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



ber\_tag\_t
LNPUBLIC **ber\_first\_element(**  

      BerElement \*ber,  

      ber\_len\_t \*len,  

      char \*\*last**);**



**Description :**



This routine
is used, along with ber\_next\_element(), to traverse a set or sequence of data
values. 


 


The
ber\_first\_element() function is used to return the tag of the first element of
a set or sequence of data values. It also returns the last byte of a set or
sequence of data values. This "last" parameter should be passed to
subsequent calls to ber\_next\_element(), which returns similar information,
namely the tag of the next element to be parsed and the last element in a set
or sequence of data values.


 


The len and
last values should not be used by applications other than as arguments to
ber\_next\_element().


 


Implemented
as a macro:


 


#define
ber\_first\_element(ber, len, last)        ND\_ber\_first\_element((ber), (len),
(last))


 


**Parameters :**



Input :  

ber  -  This state pointer points at the start of the first element to be
parsed in the set or sequence of data values.    

  

len  -  The length of the element to be parsed.  

  




Output :  

(routine)  -  Returns the tag of the first element to be parsed. LBER\_DEFAULT
is returned if the set or sequence of data values is empty.  

  

  

last  -  The last byte of a set or sequence of data values.  

  




 **See Also :**


**[BerElement](BerElement.md)**


**[ber\_len\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5E4AA411D51AEE8685256ACB0066FB61)**


**[ber\_next\_element](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BE90960005427DE885256F5C00486F06)**


**[ber\_tag\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/55264E307F9D5DE285256ACB0066B45C)**



----------------------------------------------------------------------------------------------------------


 





