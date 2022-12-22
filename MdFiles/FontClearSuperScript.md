




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



**Function : Font**



**FontClearSuperScript** **- Turns off
the SUPERSCRIPT attribute in the specified FONTID**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



FONTID **FontClearSuperScript(**  

      FONTID  fontid**);**



**Description :**



Implemented
as a macro:  

  

#define FontClearSuperScript(fontid) ((DWORD)(fontid) & ~(ISSUPER <<
FONT\_STYLE\_SHIFT))


 


**Parameters :**



Input :  

fontid  -  The FONTID in which to clear the SUPERSCRIPT attribute  

  




Output :  

(routine)  -  The specified FONTID with the SUPERSCRIPT attribute turned off  

  

  




 **See Also :**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[FontIsSuperScript](FontIsSuperScript.md)**


**[FontSetSuperScript](FontSetSuperScript.md)**



----------------------------------------------------------------------------------------------------------


 





