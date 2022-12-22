




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



**NLS\_goto\_next** **- Advances
a string pointer past one character unless it's the termination character.**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



WORD
LNPUBLIC **NLS\_goto\_next(**  

      BYTE far \* far \*ppString,  

      WORD  Len,  

      NLS\_PINFO  pInfo**);**



**Description :**



Advances a
string pointer past one character unless it's the termination character.


 


**Parameters :**



Input :  

ppString  -  A pointer to a pointer to a character in a string.  

  

Len  -  The number of bytes in the string. If the string is null terminated,
you may set this to NLS\_NULLTERM.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  

  




Output :  

(routine)  -  The size (in bytes) of the character that we advanced past. If
either of the input pointers are invalid, or if Len  is 0, this function will
return 0.  

  

  

ppString  -  A pointer to a pointer to the next character in the string.  

  




 **See Also :**


**[NLS\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/217FFE9B873C6C87852561C000787283)**


**[NLS\_PINFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**


**[OSGetLMBCSCLS](OSGetLMBCSCLS.md)**



----------------------------------------------------------------------------------------------------------


 





