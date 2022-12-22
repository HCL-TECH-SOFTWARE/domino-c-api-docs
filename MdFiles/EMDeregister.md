




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




**Initial Release 4.0**



**Function : Extension Manager**



**EMDeregister** **-
Deregisters functions from Extension Manager**


**----------------------------------------------------------------------------------------------------------**



**#include <extmgr.h>**



STATUS
LNPUBLIC **EMDeregister(**  

      HEMREGISTRATION  hRegistration**);**



**Description :**



All
functions registered to the Extension Manager must be deregistered using the
registration handle that was returned from EMRegister.


 


**Parameters :**



Input :  

hRegistration  -  Handle returned from call to EMRegister()  

  




Output :  

(routine)  -  Returns status codes from Domino or Notes core.  

NOERROR  

ERR\_ILLEGALEXT  

  

  




 **See Also :**


**[EMRegister](EMRegister.md)**



----------------------------------------------------------------------------------------------------------


 





