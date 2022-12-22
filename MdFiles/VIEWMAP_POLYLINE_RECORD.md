




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



**VIEWMAP\_POLYLINE\_RECORD** **-** Navigator
multiple-point line graphic CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   VMODSbigobj DRobj;


   WORD       
LineColor;


   WORD       
LineStyle;  

   WORD        LineWidth;  

   WORD        nPts;  

   DWORD       spare[4]; /\* for future use \*/  

} VIEWMAP\_POLYLINE\_RECORD;


 


**Description :**



Note:  The
signature for this record has changed in Release 4.5 of Domino from a byte
signature to a word signature.  The common fields structure has been changed
from VMODSdrobj to VMODSbigobj.


 


The
VIEWMAP\_POLYLINE\_RECORD stores a line defined by multiple points in a
Navigator.  This record is stored in items of type TYPE\_VIEWMAP\_LAYOUT, the
graphical layout of the Navigator.  The fields in this structure are:


 


DRObj                    Common
fields, including VIEWMAP\_POLYLINE\_RECORD signature.   See VMODSbigobj.


LineColor    Color
of the line.   Use NOTES\_COLOR\_xxx value.


LineStyle    Style
for the line.   Use VM\_LINE\_xxx value.


LineWidth   Width
of the line.


nPts                       Number
of points defining the line.


spare                      Reserved; 
must be 0.


 


This
structure is followed by the name and the display label (if any) in packed
format (no terminating NUL), then by an array of pairs of LONG values
containing the coordinates for the line.  The number of pairs of values in this
array is specified by the nPts field.


 **See Also :**


**[VMODSbigobj](VMODSbigobj.md)**



----------------------------------------------------------------------------------------------------------


 





