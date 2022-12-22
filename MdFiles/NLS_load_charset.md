




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




**Initial Release 5.0**



**Function : Character Manipulation**



**NLS\_load\_charset** **- Loads a
given character set.**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



NLS\_STATUS
LNPUBLIC **NLS\_load\_charset(**  

      WORD  CSID,  

      NLS\_PINFO FAR \*ppInfo**);**



**Description :**



This
function will load a character set and return  a pointer to a pointer to an
NLS\_INFO structure.  The calling application is responsible for unloading the
character set using NLS\_unload\_charset.


 


**Parameters :**



Input :  

CSID  -  A character set ID.  For information regarding valid character set
IDs, please see symbolic value NLS\_CS\_xxx.   

  




Output :  

(routine)  -  NLS\_SUCCESS  

NLS\_INVALIDTABLE - A table contained in the NLS\_INFO structure of the specified
character set is invalid.  

  

  

ppInfo  -  A pointer to a pointer to a populated NLS\_INFO structure.  

  




 **See Also :**


**[NLS\_CS\_xxx](NLS_CS_xxx.md)**


**[NLS\_PINFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**


**[NLS\_translate](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/155C97DCEEF0C3EE8525662800461D66)**


**[NLS\_unload\_charset](NLS_unload_charset.md)**



----------------------------------------------------------------------------------------------------------


 





