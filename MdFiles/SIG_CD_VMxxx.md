




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



**Symbolic Value : Navigators**



**SIG\_CD\_VMxxx** **-** Signatures
for items of type TYPE\_VIEWMAP\_LAYOUT.


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**


 **Symbolic Values :**      SIG\_CD\_VMHEADER           -  VIEWMAP\_HEADER\_RECORD - the
header record for the layout of a Navigator.  

  

      SIG\_CD\_VMBITMAP            -  VIEWMAP\_BITMAP\_RECORD defining a bitmap.  

  

      SIG\_CD\_VMRECT    -  VIEWMAP\_RECT\_RECORD defining a rectangle.  

  

      SIG\_CD\_VMPOLYGON        -  VIEWMAP\_POLYGON\_RECORD defining a polygon.  

  

      SIG\_CD\_VMPOLYLINE         -  VIEWMAP\_POLYLINE\_RECORD defining a line made
up of multiple segments.  

  

      SIG\_CD\_VMREGION            -  VIEWMAP\_REGION\_RECORD defining a rectangle
hotspot region.  

  

      SIG\_CD\_VMACTION            -  VIEWMAP\_ACTION\_RECORD containing action to
be performed from the Navigator.  

  

      SIG\_CD\_VMELLIPSE           -  VIEWMAP\_RECT\_RECORD defining an ellipse.  

  

      SIG\_CD\_VMRNDRECT        -  VIEWMAP\_RECT\_RECORD defining a rounded
rectangle.  

  

      SIG\_CD\_VMBUTTON           -  VIEWMAP\_RECT\_RECORD defining a button.  

  

      SIG\_CD\_VMTEXTBOX         -  VIEWMAP\_TEXT\_RECORD defining a textbox.  

  

      SIG\_CD\_VMPOLYRGN         -  VIEWMAP\_POLYGON\_RECORD defining a polygon
hotspot region.  

  

      SIG\_CD\_VMCIRCLE             -  VIEWMAP\_REGION\_RECORD defining a circle.  

  




**Description :**



The
composite data (CD) records with signatures from this set are used in the
$ViewMapLayout record of a Navigator view.


 **See Also :**


**[VIEWMAP\_ACTION\_RECORD](VIEWMAP_ACTION_RECORD.md)**


**[VIEWMAP\_BITMAP\_RECORD](VIEWMAP_BITMAP_RECORD.md)**


**[VIEWMAP\_HEADER\_RECORD](VIEWMAP_HEADER_RECORD.md)**


**[VIEWMAP\_POLYGON\_RECORD](VIEWMAP_POLYGON_RECORD.md)**


**[VIEWMAP\_POLYLINE\_RECORD](VIEWMAP_POLYLINE_RECORD.md)**


**[VIEWMAP\_RECT\_RECORD](VIEWMAP_RECT_RECORD.md)**


**[VIEWMAP\_REGION\_RECORD](VIEWMAP_REGION_RECORD.md)**


**[VIEWMAP\_TEXT\_RECORD](VIEWMAP_TEXT_RECORD.md)**



----------------------------------------------------------------------------------------------------------


 





