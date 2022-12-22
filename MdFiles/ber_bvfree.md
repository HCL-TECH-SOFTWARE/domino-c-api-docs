




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



**ber\_bvfree** **- Frees a
berval structure from memory.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



void
LNPUBLIC **ber\_bvfree(**  

      struct berval \*bv**);**



**Description :**



This routine
frees a berval structure from memory.


 


Implemented
as a macro:


 


#define
ber\_bvfree(bv)                    ND\_ber\_bvfree((bv))


 


**Parameters :**



Input :  

bv  -  Pointer to the berval structure that you want to free from memory.  

  




Output :  

(routine)  -  None.  

  

  




 **See Also :**


**[Berval](Berval.md)**



----------------------------------------------------------------------------------------------------------


 





