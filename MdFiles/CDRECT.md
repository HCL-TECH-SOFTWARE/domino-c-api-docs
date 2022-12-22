




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




**Initial Release 5.0**



**Data Type : Composite Data; Rich
Text**



**CDRECT** **-** Coordinates
of a rectangle or circle within an AREA element.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   LONG left;  

   LONG top;  

   LONG right;  

   LONG bottom;  

} CDRECT;


 


**Description :**



This structure
defines either a rectangle or a circle within a CDAREAELEMENT if the
AREA\_SHAPE\_xxx is an AREA\_SHAPE\_RECT or AREA\_SHAPE\_CIRCLE.


 **See Also :**


**[AREA\_SHAPE\_xxx](AREA_SHAPE_xxx.md)**


**[CDAREAELEMENT](CDAREAELEMENT.md)**



----------------------------------------------------------------------------------------------------------


 





