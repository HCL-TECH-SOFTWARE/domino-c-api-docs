




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Font**



**FontIsItalic** **- Returns
TRUE if the specified FONTID has the ITALIC attribute set, FALSE otherwise.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



BOOL **FontIsItalic(**  

      FONTID  fontid**);**



**Description :**



Tests to see
if the ITALIC attribute is set in the specified FONTID.  Implemented as a
macro:  

  

#define FontIsItalic(fontid) (((fontid) & ((DWORD) ISITALIC <<
FONT\_STYLE\_SHIFT)) != 0)


 


**Parameters :**



Input :  

fontid  -  The FONTID which is to be checked.  

  

  




Output :  

(routine)  -  TRUE if the ITALIC attribute is set, FALSE otherwise  

  

  




 **See Also :**


**[FontClearItalic](FontClearItalic.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[FontSetItalic](FontSetItalic.md)**



----------------------------------------------------------------------------------------------------------


 





