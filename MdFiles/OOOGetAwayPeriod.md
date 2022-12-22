




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



**OOOGetAwayPeriod** **- This
function returns time parameters that control OOO.** 


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOGetAwayPeriod(**  

      OOOCTXPTR \*pOOOContext,  

      TIMEDATE \*tdStartAway,  

      TIMEDATE \*tdEndAway**);**



**Description :**



This
function returns time parameters that control OOO. 


 


**Parameters :**



Input :  

pOOOContext  -  Pointer obtained from the OOOStartOperation call  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.  

NOERROR - Successfully performed this operation  

This function can return Domino errors.  

OOO specific errors:  

ERR\_OOO\_MISSING\_PARAM - One or more mandatory parameters were not specified  

ERR\_OOO\_MISSING\_MAILFILE - Mailfile information is not specified  

  

  

tdStartAway  -  Pointer to the date and time when Out of office will begin.  

  

tdEndAway  -  Pointer to the date and time when Out of office will end.  

  




 **See Also :**


**[OOOSetAwayPeriod](OOOSetAwayPeriod.md)**



----------------------------------------------------------------------------------------------------------


 





