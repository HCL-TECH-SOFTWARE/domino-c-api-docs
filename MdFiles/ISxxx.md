




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



**ISxxx** **-** Bit field
values for STYLE member of FONTIDFIELDS.


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**


 **Symbolic Values :**      ISBOLD        -  Text in the CDTEXT item will be in
boldface.  

  

      ISITALIC      -  Text in the CDTEXT item will be in italics.  

  

      ISUNDERLINE          -  Text in the CDTEXT item will be underlined.  

  

      ISSTRIKEOUT         -  Text in the CDTEXT item will be Struck out.  

  

      ISSUPER     -  Text in the CDTEXT item will be superscripted  

  

      ISSUB          -  Text in the CDTEXT item will be subscripted.  

  

      ISEFFECT    -  Text in the following CDTEXT item will be of a special
effect style: shadowed, embossed, or extruded.  

  

      ISSHADOW              -  Text in the following CDTEXT item will be
shadowed.  

  

      ISEMBOSS   -  Text in the following CDTEXT item will be embossed. Embossed
text is text that appears to be sticking out of the page.  

  

      ISEXTRUDE             -  Text in the following CDTEXT item will be
extruded. Extruded text is text that appears to be pushed into the page.  

  




**Description :**



These
defines are used to specify font style attributes (bold, italic, etc.) in the
FONTID field in a CDTEXT item.  These values may be combined by bitwise OR-ing
them together.


 **See Also :**


**[CDTEXT](CDTEXT.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[FONT\_FACE\_xxx](FONT_FACE_xxx.md)**


**[NOTES\_COLOR\_xxx](NOTES_COLOR_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





