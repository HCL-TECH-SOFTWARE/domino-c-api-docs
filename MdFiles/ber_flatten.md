




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



**ber\_flatten** **- Allocates
a berval struct.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



int
LNPUBLIC **ber\_flatten(**  

      BerElement \*ber,  

      struct berval \*\*bvPtr**);**



**Description :**



This routine
allocates a berval struct whose contents are a BER encoding taken from the ber
argument. The bvPtr pointer points to the returned berval structure, which
should be freed using ber\_bvfree().


  

The use of ber\_flatten on a BerElement in which all '{' and '}' format
modifiers have not been properly matched is an error (i.e., -1 will be returned
by ber\_flatten() if this situation is exists).


 


Implemented
as a macro:


 


#define
ber\_flatten(ber, bvPtr)         ND\_ber\_flatten((ber), (bvPtr))


 


**Parameters :**



Input :  

ber  -  Pointer to a BerElement structure which is encoded and stored as the
contents of the berval struct returned by this routine.  

  




Output :  

(routine)  -  0 on success and -1 on error.  

  

  

bvPtr  -  Pointer to a pointer to the returned berval structure.  

  




 **See Also :**


**[BerElement](BerElement.md)**


**[Berval](Berval.md)**



----------------------------------------------------------------------------------------------------------


 





