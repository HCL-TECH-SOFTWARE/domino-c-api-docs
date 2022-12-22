




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




**Initial Release 8.5.2**



**Function : OOO**



**OOOEndOperation** **- This
function frees memory.** 


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOEndOperation(**  

      OOOCTXHANDLE  hOOContext,  

      OOOCTXPTR \*pOOOContext**);**



**Description :**



This
function frees memory.  This function should be called after all other calls
related to a specific operation(s) are completed.


 


**Parameters :**



Input :  

hOOContext  -  Handle to the OOO context returned from OOOStartOperation call  

  

pOOOContext  -  Pointer to the OOO context returned from OOOStartOperation call  

  




Output :  

(routine)  -  Return status from this call indicates either success or what the
error is.   

NOERROR - Successfully perform this function.  

This function can return Domino errors.  

  

  




 **See Also :**


**[OOOStartOperation](OOOStartOperation.md)**



----------------------------------------------------------------------------------------------------------


 





