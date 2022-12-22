




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



**NLS\_goto\_next\_break** **- Advance a
pointer to the byte following the next word break in a string.**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



WORD
LNPUBLIC **NLS\_goto\_next\_break(**  

      BYTE far \* far \*ppString,  

      WORD  Len,  

      NLS\_PINFO  pInfo**);**



**Description :**



Advance a
pointer to the byte following the next word break in a string.


 


Note: Kanji,
Katakana and Hiragana characters are treated like words.


 


**Parameters :**



Input :  

ppString  -  A pointer to a pointer to a character in a string.  

  

Len  -  The number of bytes in the string. If the string is null terminated,
you may set this to NLS\_NULLTERM.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  

  




Output :  

(routine)  -  The number of bytes that were skipped to find the next word
break.  

  

  

ppString  -  A pointer to a pointer to the character following the next word
break.  

  




 **See Also :**


**[NLS\_goto\_next](NLS_goto_next.md)**


**[NLS\_goto\_next\_break](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3A4238A6D5F769B7852561C0007AA5A7)**


**[NLS\_goto\_next\_word\_end](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/87979E5107591749852561C0007A3EFC)**


**[NLS\_goto\_next\_word\_start](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E10F9A20E7A85B40852561C0007A6ADD)**


**[NLS\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/217FFE9B873C6C87852561C000787283)**


**[NLS\_PINFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**


**[OSGetLMBCSCLS](OSGetLMBCSCLS.md)**



----------------------------------------------------------------------------------------------------------


 





