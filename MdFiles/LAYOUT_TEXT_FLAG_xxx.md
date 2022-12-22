




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



**LAYOUT\_TEXT\_FLAG\_xxx** **-** CDLAYOUTTEXT
flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      LAYOUT\_TEXT\_FLAG\_TRANS        -  Display with a transparent
background.  

  

      LAYOUT\_TEXT\_FLAG\_LEFT            -  Left-justify text.  

  

      LAYOUT\_TEXT\_FLAG\_CENTER      -  Center text.  

  

      LAYOUT\_TEXT\_FLAG\_RIGHT         -  Right-justify text.  

  

      LAYOUT\_TEXT\_FLAG\_ALIGN\_MASK           -  Mask used to obtain only the
text alignment bits.  

  

      LAYOUT\_TEXT\_FLAG\_VCENTER    -  Center field contents vertically.  

  

      LAYOUT\_TEXT\_FLAG\_LTR             -  Left to right order text.  

  

      LAYOUT\_TEXT\_FLAG\_RTL             -  Right to left order text.  

  

      LAYOUT\_TEXT\_FLAG\_RO\_MASK    -  Read only mask.  

  

      LAYOUT\_TEXT\_FLAGS\_MASK        -  Mask used to obtain only the valid text
layout flag bits.  

  




**Description :**



These flags
are set in the "Flags" field of a CDLAYOUTTEXT record, and control
operation of the field in the layout region.


 **See Also :**


**[CDLAYOUTTEXT](CDLAYOUTTEXT.md)**



----------------------------------------------------------------------------------------------------------


 





