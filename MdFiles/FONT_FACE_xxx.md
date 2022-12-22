




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



**FONT\_FACE\_xxx** **-** BYTE values
for Face member of FONTIDFIELDS.


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**


 **Symbolic Values :**      FONT\_FACE\_ROMAN          -  Text will be displayed in a
Times Roman typeface.  

  

      FONT\_FACE\_SWISS            -  Text will be displayed in a Helvetica
typeface.  

  

      FONT\_FACE\_UNICODE       -  Text will be displayed in a Monotype Sans WT
typeface.  

  

      FONT\_FACE\_USERINTERFACE      -  Text will be displayed in an Arial
typeface.  

  

      FONT\_FACE\_TYPEWRITER            -  Text will be displayed in a Courier typeface.  

  




**Description :**



These
symbols define the standard type faces identified in the Face member of a
FONTIDFIELDS structure.  

  

The Face member of the FONTIDFIELDS structure may be either one of these
standard font faces, or a font ID resolved by a font table.  A Face member
value greater than or equal to STATIC\_FONT\_FACES (5) refers to an entry in a
font table. See Data Type CDFONTTABLE.


 **See Also :**


**[CDFONTTABLE](CDFONTTABLE.md)**


**[CDTEXT](CDTEXT.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[ISxxx](ISxxx.md)**


**[NOTES\_COLOR\_xxx](NOTES_COLOR_xxx.md)**


**[STATIC\_FONT\_FACES](STATIC_FONT_FACES.md)**



----------------------------------------------------------------------------------------------------------


 





