




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



**FontGetShadowOffset** **- Returns
the offset of the shadow relative to the text.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



BYTE **FontGetShadowOffset(**  

      FONTID  fontid**);**



**Description :**



This routine
returns the offset of the shadow.  Shadowed text is a two pass process where
the text is first drawn with the shadow color at an offset from the actual
text.  This offset is currently a fixed fraction of the font size.  The actual
text is then drawn.


 


Implemented
as a macro:


 


#define
FontGetShadowOffset(fontid) (BYTE)(FontGetSize(fontid)/(BYTE)FONT\_SHADOW\_VALUE
+ 1)


 


**Parameters :**



Input :  

fontid  -  The FONTID in which to compute the SHADOW offset.  

  




Output :  

(routine)  -  Offset, in points, from the text's position which specifies where
the shadow to the text is drawn.  

  

  




 **See Also :**


**[FontClearShadow](FontClearShadow.md)**


**[FontSetShadow](FontSetShadow.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**



----------------------------------------------------------------------------------------------------------


 





