




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



**NLS\_put\_term** **- Copy a
character from one buffer to another, then NULL-terminate the output buffer.**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



NLS\_STATUS
LNPUBLIC **NLS\_put\_term(**  

      BYTE far \* far \*ppString,  

      const BYTE far \*pCharacter,  

      NLS\_PINFO  pInfo**);**



**Description :**



Copy a
character from one buffer to another, and append a NULL character to the output
buffer after the copied character. After the function completes, the pointer to
the input/output string will be incremented to point to the NULL character.


 


**Parameters :**



Input :  

ppString  -   A pointer to a pointer to the location at which to write the
character referenced by the pCharacter argument.  

  

pCharacter  -  A pointer to the character that is to be copied to the location
referenced by the ppString argument.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  

  




Output :  

(routine)  -  NLS\_SUCCESS - the operation completed successfully.  

  

  

ppString  -  A pointer to a pointer to the character following the one that was
written.  

  




 **See Also :**


**[NLS\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/217FFE9B873C6C87852561C000787283)**


**[NLS\_PINFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**


**[NLS\_put](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85E1A3E0216850CB8525624A00613369)**


**[OSGetLMBCSCLS](OSGetLMBCSCLS.md)**



----------------------------------------------------------------------------------------------------------


 





