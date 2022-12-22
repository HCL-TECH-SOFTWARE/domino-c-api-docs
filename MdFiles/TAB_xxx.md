




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



**Symbolic Value : Rich Text**



**TAB\_xxx** **-** Paragraph
tab codes.


**----------------------------------------------------------------------------------------------------------**



**#include <editdflt.h>**


 **Symbolic Values :**      TAB\_LEFT   -  Default - text is left justied starting at the
tab position.  

  

      TAB\_RIGHT             -  Text is right justified before the tab position.  

  

      TAB\_DECIMAL         -  Text is placed so that the decimal point is
aligned with the tab position.  

  

      TAB\_CENTER          -  Text is centered around the tab position.  

  

      TAB\_DEFAULT        -  TAB\_LEFT  

  




**Description :**



Possible
2-bit values for the TabTypes member of the CDPABDEFINITION structure, which
indicates the placement of text within a tab position.  You specify a 2-bit tab
type for each tab.


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**



----------------------------------------------------------------------------------------------------------


 





