




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



**OOOSetExcludeInternet** **- This
function sets a flag which defines how to treat internet emails.** 


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOSetExcludeInternet(**  

      OOOCTXPTR \*pOOOContext,  

      BOOL  bExcludeInternet**);**



**Description :**



This
function sets a flag which defines how to treat internet emails.  This
functional call is optional.   If this flag is set to TRUE OOO notifications
will not be generated for email originating from the internet.  The default for
this flag is TRUE.


 


**Parameters :**



Input :  

pOOOContext  -  Pointer obtained from the OOOStartOperation call  

  

bExcludeInternet  -  Flag to ignore internet emails when set to TRUE  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   

NOERROR - Successfully performed this operation  

  

  




 **See Also :**


**[OOOGetExcludeInternet](OOOGetExcludeInternet.md)**



----------------------------------------------------------------------------------------------------------


 





