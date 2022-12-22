




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



**VIEWMAP\_STYLE\_DEFAULTS** **-** Default
settings for Navigator elements.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   VIEWMAP\_SHAPE\_DEFAULTS   Shapes;  

   VIEWMAP\_LINE\_DEFAULTS    Lines;  

   VIEWMAP\_REGION\_DEFAULTS  Regions;  

   VIEWMAP\_BUTTON\_DEFAULTS  Buttons;  

   VIEWMAP\_BITMAP\_DEFAULTS  Bitmaps;  

   VIEWMAP\_TEXTBOX\_DEFAULTS TextBoxes;  

} VIEWMAP\_STYLE\_DEFAULTS;


 


**Description :**



The
VIEWMAP\_STYLE\_DEFAULTS structure stores the default settings for the display of
graphical elements in a Navigator.  This structure contains the other
VIEWMAP\_xxx\_DEFAULTS records.  This structure is, in turn, a component of a
VIEWMAP\_DATASET\_RECORD CD record.


 **See Also :**


**[VIEWMAP\_SHAPE\_DEFAULTS](VIEWMAP_SHAPE_DEFAULTS.md)**


**[VIEWMAP\_LINE\_DEFAULTS](VIEWMAP_LINE_DEFAULTS.md)**


**[VIEWMAP\_REGION\_DEFAULTS](VIEWMAP_REGION_DEFAULTS.md)**


**[VIEWMAP\_BUTTON\_DEFAULTS](VIEWMAP_BUTTON_DEFAULTS.md)**


**[VIEWMAP\_BITMAP\_DEFAULTS](VIEWMAP_BITMAP_DEFAULTS.md)**


**[VIEWMAP\_TEXTBOX\_DEFAULTS](VIEWMAP_TEXTBOX_DEFAULTS.md)**


**[VIEWMAP\_DATASET\_RECORD](VIEWMAP_DATASET_RECORD.md)**



----------------------------------------------------------------------------------------------------------


 





