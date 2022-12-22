




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



**NLS\_find\_substr** **- Search a
string for a given substring.**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



NLS\_STATUS
LNPUBLIC **NLS\_find\_substr(**  

      BYTE far \* far \*ppString,  

      WORD  Len1,  

      const BYTE far \*pSubString,  

      WORD  Len2,  

      NLS\_PINFO  pInfo**);**



**Description :**



This
function searches a string for a given substring, returning a pointer to the
start of the substring within the original string. The search is case sensitive
and pitch sensitive.


 


**Parameters :**



Input :  

ppString  -  A pointer to a pointer to the string to be searched.  

  

Len1  -  The number of characters in the string to be searched.  

  

pSubString  -  The substring for which to search.  

  

Len2  -  The number of characters in the substring for which to search.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set.  The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  

  




Output :  

(routine)  -  NLS\_SUCCESS - The substring was found in the string, or the
substring was empty.  

NLS\_BADPARM - The string, the substring, or the NLS\_INFO structure specified in
the function call was invalid.  

NLS\_FINDFAILED - The string was empty, or the substring was not found in the
string.  

NLS\_INVALIDTABLE - One of the tables in the specified NLS\_INFO structure is
invalid.  

  

  

ppString  -  A pointer to a pointer to the substring within the original
string.  

  




 **See Also :**


**[NLS\_find](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/50155DCE368D5A4B8525624A0060868C)**


**[NLS\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/217FFE9B873C6C87852561C000787283)**


**[OSGetLMBCSCLS](OSGetLMBCSCLS.md)**



----------------------------------------------------------------------------------------------------------


 





