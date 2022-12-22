




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




**Initial Release 4.1**



**Symbolic Value : Rich Text**



**LAYOUT\_FLAG\_xxx** **-** CDLAYOUT
Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      LAYOUT\_FLAG\_SHOWBORDER      -  Display the border for the
layout region.  

  

      LAYOUT\_FLAG\_SHOWGRID            -  Display the grid when designing the
form.  

  

      LAYOUT\_FLAG\_SNAPTOGRID        -  Force layout elements to be located on
grid coordinates.  

  

      LAYOUT\_FLAG\_3DSTYLE    -  Use 3D effects when drawing layout elements.  

  

      LAYOUT\_FLAG\_RTL            -  Layout elements right to left.  

  

      LAYOUT\_FLAG\_DONTWRAP           -  Do not wrap elements.  

  




**Description :**



These flags
are set in the "Flags" field of a CDLAYOUT record, and control
options for operation of the layout region.


 **See Also :**


**[CDLAYOUT](CDLAYOUT.md)**



----------------------------------------------------------------------------------------------------------


 





