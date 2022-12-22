




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Data Type : Views**



**VIEW\_MONTH\_FORMAT** **-** Header
structure used in VIEW\_CALENDAR\_FORMAT


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct {  

   VIEW\_FORMAT\_HEADER Header;  

} VIEW\_MONTH\_FORMAT;


 


**Description :**



This defines
the structure of a header member of the VIEW\_CALENDAR\_FORMAT structure.  The
VIEW\_CALENDAR\_FORMAT structure is part of a VIEW\_CALENDAR\_FORMAT\_ITEM, which is
an item in a calendar view note.  The structure is the same as the
VIEW\_FORMAT\_HEADER structure.


 **See Also :**


**[VIEW\_FORMAT\_HEADER](VIEW_FORMAT_HEADER.md)**


**[VIEW\_CALENDAR\_FORMAT](VIEW_CALENDAR_FORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





