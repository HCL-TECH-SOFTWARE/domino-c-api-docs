




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



**ber\_bvecfree** **- Frees an
array of berval structures.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



void
LNPUBLIC **ber\_bvecfree(**  

      struct berval \*\*bv**);**



**Description :**



Frees an
array of berval structures. Each of the berval structures in the array are
freed using ber\_bvfree(), then the array itself is freed.


 


Implemented
as a macro:


 


#define
ber\_bvecfree(bv)     ND\_ber\_bvecfree((bv))


 


**Parameters :**



Input :  

bv  -  A pointer to a pointer to an array of berval structures.  

  




Output :  

(routine)  -  None.  

  

  




 **See Also :**


**[Berval](Berval.md)**


**[ber\_bvfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6E60A0A308298A3985256F5C00486F08)**



----------------------------------------------------------------------------------------------------------


 





