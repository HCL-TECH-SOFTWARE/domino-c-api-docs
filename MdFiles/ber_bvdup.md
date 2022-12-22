




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



**ber\_bvdup** **- Creates a
new copy of a berval structure based on the original.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



struct
berval \* LNPUBLIC **ber\_bvdup(**  

      const struct berval \*bv**);**



**Description :**



This
function creates a new copy of a berval structure based on the one supplied in
bv. The bv\_val field in the returned berval structure points to a different
area of memory than the bv\_val field in the bv argument.  The NULL pointer is
returned on error (e.g. out of memory).


 


Implemented
as a macro:


 


#define
ber\_bvdup(bv)         ND\_ber\_bvdup((bv))


 


**Parameters :**



Input :  

bv  -   Pointer to the original berval structure.  

  




Output :  

(routine)  -   Pointer to the new berval structure.  

  

  




 **See Also :**


**[Berval](Berval.md)**



----------------------------------------------------------------------------------------------------------


 





