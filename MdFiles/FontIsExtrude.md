




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.5**



**Function : Font**



**FontIsExtrude** **- Returns
TRUE if the specified FONTID has the EXTRUDE attribute set, FALSE otherwise.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



BOOL **FontIsExtrude(**  

      FONTID  fontid**);**



**Description :**



This routine
tests if the EXTRUDE attribute is set in the specified FONTID.  Text that has
the EXTRUDE attribute appears to be pushed into the page.


 


Implemented
as a macro:


 


#define
FontIsExtrude(fontid) (((fontid) & ((DWORD) ISEXTRUDE <<
FONT\_STYLE\_SHIFT)) == ((DWORD) ISEXTRUDE << FONT\_STYLE\_SHIFT))


 


**Parameters :**



Input :  

fontid  -  The FONTID which is to be checked for the EXTRUDE attribute.  

  




Output :  

(routine)  -  TRUE if the EXTRUDE attribute is set, FALSE otherwise  

  

  




 **See Also :**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[FontClearExtrude](FontClearExtrude.md)**


**[FontSetExtrude](FontSetExtrude.md)**



----------------------------------------------------------------------------------------------------------


 





