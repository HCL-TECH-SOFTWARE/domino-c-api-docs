




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



**Function : Character Manipulation**



**OSGetNativeCLS** **- Returns
an NLS\_INFO struct containing information about the native (machine-specific)
character set.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmisc.h>**



NLS\_PINFO
LNPUBLIC **OSGetNativeCLS(**void**);**



**Description :**



This
function returns an NLS\_INFO struct containing information about the native
character set. If for some reason your application needed to manipulate text in
the platform's native character set rather than in LMBCS, The NLS\_INFO struct
could then be used in subsequent calls to other NLS functions.


 


**Parameters :**




Output :  

(routine)  -  A pointer to an NLS\_INFO struct.  

  

  




 **See Also :**


**[NLS\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/217FFE9B873C6C87852561C000787283)**


**[NLS\_PINFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**


**[OSGetLMBCSCLS](OSGetLMBCSCLS.md)**



----------------------------------------------------------------------------------------------------------


 





