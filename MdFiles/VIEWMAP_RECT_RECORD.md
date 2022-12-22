




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



**VIEWMAP\_RECT\_RECORD** **-** Navigator
rectangle graphic CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   VMODSdrobj DRobj;


   WORD      
LineColor;  

   WORD       FillFGColor;  

   WORD       FillBGColor;


   WORD      
LineStyle;  

   WORD       LineWidth;  

   WORD       FillStyle;  

   DWORD      spare[4]; /\* for future use \*/  

} VIEWMAP\_RECT\_RECORD;


 


**Description :**



The
VIEWMAP\_RECT\_RECORD stores a rectangle graphic (includes Rectangle, Ellipse,
Round Rectangel, and Button objects) in a Navigator.  This record is stored in
items of type TYPE\_VIEWMAP\_LAYOUT, the graphical layout of the Navigator.  The
fields in this structure are:


 


DRObj              Common
fields, including VIEWMAP\_RECT\_RECORD signature.   See VMODSdrobj.


LineColor          Color
of the boundary line.   Use NOTES\_COLOR\_xxx value.


FillFGColor       Foreground
fill color.   Use NOTES\_COLOR\_xxx value.  


FillBGColor       Background
fill color.   Use NOTES\_COLOR\_xxx value.


LineStyle          Style
for the boundary line.   Use VM\_LINE\_xxx value.


LineWidth         Width
of the boundary line.


FillStyle            Style
of rectangle fill.   Use VM\_FILL\_xxx value.


spare                Reserved; 
must be 0.


 


This
structure is followed by the name and the display label (if any, as defined by
DRObj) in packed format (no terminating NUL).


 **See Also :**


**[VMODSdrobj](VMODSdrobj.md)**



----------------------------------------------------------------------------------------------------------


 





