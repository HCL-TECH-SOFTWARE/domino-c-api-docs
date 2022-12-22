




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



**VIEWMAP\_BUTTON\_DEFAULTS** **-** Default
settings for Navigator buttons.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   VIEWMAP\_HIGHLIGHT\_DEFAULTS Highlight;  

   WORD   LineColor;  

   WORD   FillFGColor;  

   WORD   FillBGColor;  

   WORD   LineStyle;  

   WORD   LineWidth;  

   WORD   FillStyle;  

   FONTID FontID;  

} VIEWMAP\_BUTTON\_DEFAULTS;


 


**Description :**



The
VIEWMAP\_BUTTON\_DEFAULTSstructure contains default attributes for buttons in the
Navigator.  This structure is a component of the VIEWMAP\_STYLE\_DEFAULTS
structure, which in turn is stored in the VIEWMAP\_DATASET\_RECORD.  The fields
in this structure are:


 


Highlight           Default
highlight settings.


LineColor          Default
line color.


FillFGColor       Default
fill color for foreground.


FillBGColor       Default
fill color for background.


LineStyle          Default
line style.


LineWidth         Default
line width.


FillStyle Default
fill style.


FontID              Default
Font ID for button text.


 


 **See Also :**


**[VIEWMAP\_STYLE\_DEFAULTS](VIEWMAP_STYLE_DEFAULTS.md)**


**[VIEWMAP\_HIGHLIGHT\_DEFAULTS](VIEWMAP_HIGHLIGHT_DEFAULTS.md)**



----------------------------------------------------------------------------------------------------------


 





