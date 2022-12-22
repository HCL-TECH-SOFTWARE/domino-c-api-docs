




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



**LAYOUT\_FIELD\_TYPE\_xxx** **-** Type of
layout field for a CDLAYOUTFIELD record.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      LAYOUT\_FIELD\_TYPE\_TEXT          -  Present as a text box,
either editable or non-editable.  

  

      LAYOUT\_FIELD\_TYPE\_CHECK       -  Present as a checkbox.  

  

      LAYOUT\_FIELD\_TYPE\_RADIO        -  Present as a "radio-button"
box.  

  

      LAYOUT\_FIELD\_TYPE\_LIST            -  Present as a listbox.  

  

      LAYOUT\_FIELD\_TYPE\_COMBO      -  Present as a "combo" box.  

  




**Description :**



The
bFieldType member of a CDLAYOUTFIELD record specifies the user interface for a
field.


 **See Also :**


**[CDLAYOUTFIELD](CDLAYOUTFIELD.md)**



----------------------------------------------------------------------------------------------------------


 





