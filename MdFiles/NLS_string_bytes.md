




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



**NLS\_string\_bytes** **- Returns
the number of bytes in a string.**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



NLS\_STATUS
LNPUBLIC **NLS\_string\_bytes(**  

      const BYTE far \*pString,  

      WORD  NumChars,  

      WORD far \*pNumBytes,  

      NLS\_PINFO  pInfo**);**



**Description :**



Returns the
number of bytes in a string. If a multibyte character set is in use, the number
of bytes in a string will likely be larger than the number of characters in a
string.


 


**Parameters :**



Input :  

pString  -  A pointer to a string in which the bytes are to be counted.  

  

NumChars  -  The number of characters in a string. If the string is
null-terminated, specifying NLS\_NULLTERM for this argument will make the
function work more efficiently. Note: if you pass in NLS\_NULLTERM for this
argument, the function returns a byte count that includes the NULL
terminator.       

  

pNumBytes  -  A pointer to a WORD to receive the byte count.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  

  




Output :  

(routine)  -  NLS\_SUCCESS - the operation completed successfully.  

  

  

pNumBytes  -  A pointer to a WORD containing the number of bytes in the string.  

  




 **See Also :**


**[NLS\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/217FFE9B873C6C87852561C000787283)**


**[NLS\_PINFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**


**[NLS\_string\_chars](NLS_string_chars.md)**


**[OSGetLMBCSCLS](OSGetLMBCSCLS.md)**



----------------------------------------------------------------------------------------------------------


 





