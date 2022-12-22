




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




**Initial Release 4.0**



**Data Type : Navigators**



**VIEWMAP\_HIGHLIGHT\_DEFAULTS** **-** Default
highlight settings for Navigator elements.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   WORD   bHighlightTouch;  

   WORD   bHighlightCurrent;  

   WORD   HLOutlineColor;  

   WORD   HLOutlineWidth;  

   WORD   HLOutlineStyle;  

   WORD   HLFillColor;      

} VIEWMAP\_HIGHLIGHT\_DEFAULTS;


 


**Description :**



The
VIEWMAP\_HIGHLIGHT\_DEFAULTS structure stores default settings for highlighting
the graphical elements of a Navigator.  This structure is common to all the
VIEWMAP\_xxx\_DEFAULTS structures.  The fields in this structure are:


 


bHighlightTouch           If
TRUE, highlight elements when touched.


bHighlightCurrent          If
TRUE, highlight when element is the current element.


HLOutlineColor             Color
to use for the outline of a highlighted element.


HLOutlineWidth Width
of the outline of a highlighted element.


HLOutlineStyle              Style
for the outline of a highlighted element.


HLFillColor                   Fill
color to use for a highlighted element.


 


 **See Also :**


**[VIEWMAP\_SHAPE\_DEFAULTS](VIEWMAP_SHAPE_DEFAULTS.md)**


**[VIEWMAP\_LINE\_DEFAULTS](VIEWMAP_LINE_DEFAULTS.md)**


**[VIEWMAP\_REGION\_DEFAULTS](VIEWMAP_REGION_DEFAULTS.md)**


**[VIEWMAP\_BUTTON\_DEFAULTS](VIEWMAP_BUTTON_DEFAULTS.md)**


**[VIEWMAP\_BITMAP\_DEFAULTS](VIEWMAP_BITMAP_DEFAULTS.md)**


**[VIEWMAP\_TEXTBOX\_DEFAULTS](VIEWMAP_TEXTBOX_DEFAULTS.md)**



----------------------------------------------------------------------------------------------------------


 





