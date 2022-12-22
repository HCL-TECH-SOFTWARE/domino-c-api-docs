




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



**NLS\_islower** **- Tests if
a character is a lowercase alphabetic character.**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



NLS\_STATUS
LNPUBLIC **NLS\_islower(**  

      const BYTE far \*pCharacter,  

      NLS\_PINFO  pInfo**);**



**Description :**



This
function tests if a character is a lowercase alphabetic character.


 


**Parameters :**



Input :  

pCharacter  -  Pointer to the character to be tested.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  

  




Output :  

(routine)  -  NLS\_SUCCESS - The specified character is a lowercase alphabetic
character.  

NLS\_PROPNOTFOUND - The specified character is NOT a lowercase alphabetic
character.  

NLS\_INVALIDTABLE - pInfo->PropertyTable is NULL;  

  

  




 **See Also :**


**[NLS\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/217FFE9B873C6C87852561C000787283)**


**[NLS\_isalnum](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9B0DEB96658335578525624A0060DA94)**


**[NLS\_isalpha](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/47DB676D04D6779B8525623600583E55)**


**[NLS\_isarith](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/89BC757CE8E60F5C85256236005708AE)**


**[NLS\_iscntrl](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/732A1DC3535E76DC8525623600585FE1)**


**[NLS\_isdigit](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/AC23F12FD99C7859852562360058614C)**


**[NLS\_isleadbyte](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9F81710E22AD976385256236005862AA)**


**[NLS\_ispunct](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5D3BA25EF320EC31852562360058658B)**


**[NLS\_isspace](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0E3C8C2005C054EE8525623600586435)**


**[NLS\_isupper](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BEEE73E750EFAD3785256236005866FB)**


**[NLS\_PINFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**


**[OSGetLMBCSCLS](OSGetLMBCSCLS.md)**



----------------------------------------------------------------------------------------------------------


 





