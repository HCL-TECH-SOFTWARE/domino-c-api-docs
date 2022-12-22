




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



**Symbolic Value : Extension Manager**



**EM\_REG\_xxx** **-** EMRegister()
option flags


**----------------------------------------------------------------------------------------------------------**



**#include <extmgr.h>**


 **Symbolic Values :**      EM\_REG\_BEFORE   -  Call the hook before Domino or Notes core
operation.  

  

      EM\_REG\_AFTER     -  Call the hook after Domino or Notes core operation.  

  




**Description :**



These flag
values are passed to EMRegister() to indicate whether the callback function is
to be called before or after Domino or Notes completes the core processing for
this operation.  These two flags may be combined to indicate that the callback
should be called both before and after core processing.


 **See Also :**


**[EMRegister](EMRegister.md)**



----------------------------------------------------------------------------------------------------------


 





