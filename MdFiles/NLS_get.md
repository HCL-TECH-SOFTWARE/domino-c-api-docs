




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



**NLS\_get** **- Retrieves
a character given a pointer to it, and also advances the pointer**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



NLS\_STATUS
LNPUBLIC **NLS\_get(**  

      BYTE far \* far \*ppString,  

      WORD  Len,  

      BYTE far \*pCharacter,  

      NLS\_PINFO  pInfo**);**



**Description :**



Given a
pointer to a character in a string, this function retrieves the character,
advancing the pointer to the next character in the string.


 


**Parameters :**



Input :  

ppString  -  A pointer to a pointer to a character in a string.  

  

Len  -  The number of characters in the ppString.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  

  




Output :  

(routine)  -  NLS\_SUCCESS  

NLS\_BADPARM - The string, the character, or the NLS\_INFO structure specified in
the function call was invalid.  

NLS\_ENDOFSTRING - the string was empty.  

  

  

ppString  -  A pointer to a pointer to the next character in the string.  

  

pCharacter  -  The character that was read from the string.  

  




 **See Also :**


**[NLS\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/217FFE9B873C6C87852561C000787283)**


**[OSGetLMBCSCLS](OSGetLMBCSCLS.md)**



----------------------------------------------------------------------------------------------------------


 





