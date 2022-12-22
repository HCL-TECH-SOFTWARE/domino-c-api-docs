




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



**ber\_peek\_tag** **- Returns
the tag of the next element to be parsed.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



ber\_tag\_t
LNPUBLIC **ber\_peek\_tag(**  

      BerElement \*ber,  

      ber\_len\_t \*len**);**



**Description :**



This routine
returns the tag of the next element to be parsed.  The decoding position within
the ber argument is unchanged by this call; that is, the fact that
ber\_peek\_tag() has been called does not affect future use of ber.


 


 


Implemented
as a macro:


 


#define
ber\_peek\_tag(ber, len)        ND\_ber\_peek\_tag((ber), (len))


 


**Parameters :**



Input :  

ber  -  This state pointer points at the tag of the next element to be parsed.  

  

len  -  The length of the element to be parsed.  

  




Output :  

(routine)  -  The tag of the next element to be parsed.  

  

LBER\_DEFAULT is returned if there is no further data to be read.    

  

  




 **See Also :**


**[BerElement](BerElement.md)**


**[ber\_len\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5E4AA411D51AEE8685256ACB0066FB61)**


**[ber\_tag\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/55264E307F9D5DE285256ACB0066B45C)**



----------------------------------------------------------------------------------------------------------


 





