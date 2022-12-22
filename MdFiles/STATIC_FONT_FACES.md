




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




 


**Symbolic Value : Miscellaneous**



**STATIC\_FONT\_FACES** **-** Used to
determine whether a font table entry for a specified font must be generated.


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



**Description :**



The symbols
FONT\_FACE\_xxx define the standard type faces identified in the Face member of a
FONTIDFIELDS structure.  The Face member of the FONTIDFIELDS structure may be
any one of these standard font faces, or a font ID resolved by a font table.  A
Face member value greater than or equal to STATIC\_FONT\_FACES (5) refers to an
entry in a font table.  See Data Type CDFONTTABLE.


 **See Also :**


**[CDFONTTABLE](CDFONTTABLE.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[FONT\_FACE\_xxx](FONT_FACE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





