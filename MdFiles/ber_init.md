




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



**ber\_init** **-
Constructs a BerElement structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



BerElement
\* LNPUBLIC **ber\_init(**  

      const struct berval \*bv**);**



**Description :**



This
function constructs a BerElement structure and returns a new BerElement
containing a copy of the data in the bv argument.  


 


Implemented
as a macro:


 


#define
ber\_init(bv)             ND\_ber\_init((bv))


 


**Parameters :**



Input :  

bv  -  Pointer to a berval structure, a copy of which is stored in the
BerElement struct returned by this routine.  

  




Output :  

(routine)  -  Pointer to a BerElement structure. This routine returns the NULL
pointer on error.  

  

  




 **See Also :**


**[BerElement](BerElement.md)**


**[Berval](Berval.md)**



----------------------------------------------------------------------------------------------------------


 





