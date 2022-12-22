




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



**LAYOUT\_FIELD\_FLAG\_xxx** **-** CDLAYOUTFIELD
flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      LAYOUT\_FIELD\_FLAG\_SINGLELINE            -  Draw the border
with a single line.  

  

      LAYOUT\_FIELD\_FLAG\_VSCROLL    -  Allow vertical scrolling in the field.  

  

      LAYOUT\_FIELD\_FLAG\_MULTISEL   -  Allow multiple selections within the
field if the field is a listbox or checkbox.  

  

      LAYOUT\_FIELD\_FLAG\_STATIC       -  Field content is static (cannot be
edited).  

  

      LAYOUT\_FIELD\_FLAG\_NOBORDER            -  Do not draw a border.  

  

      LAYOUT\_FIELD\_FLAG\_IMAGE        -  Field is displayed as an image, not as
text.  

  

The following flags must be the same as LAYOUT\_TEXT\_FLAG\_xxx equivalents:  

  

      LAYOUT\_FIELD\_FLAG\_LTR             -  Text Left to Right  

  

      LAYOUT\_FIELD\_FLAG\_RTL             -  Text Right to Left  

  

      LAYOUT\_FIELD\_FLAG\_TRANS        -  Display with a transparent background.  

  

      LAYOUT\_FIELD\_FLAG\_LEFT           -  Left-justify text.  

  

      LAYOUT\_FIELD\_FLAG\_CENTER     -  Center text.  

  

      LAYOUT\_FIELD\_FLAG\_RIGHT         -  Right-justify text.  

  

      LAYOUT\_FIELD\_FLAG\_VCENTER   -  Center field contents vertically.  

  




**Description :**



These flags
are set in the "Flags" field of a CDLAYOUTFIELD record, and control
options for operation of the field in the layout region.


 **See Also :**


**[CDLAYOUTFIELD](CDLAYOUTFIELD.md)**



----------------------------------------------------------------------------------------------------------


 





