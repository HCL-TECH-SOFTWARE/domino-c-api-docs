




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




 


**Data Type : Time**



**TIME** **-** Binary
time/date and its integer components.


**----------------------------------------------------------------------------------------------------------**



**#include
<misc.h>**



**Definition :**



typedef struct {  

   int year;       /\* 1-32767 \*/  

   int month;      /\* 1-12 \*/  

   int day;        /\* 1-31 \*/  

   int weekday;    /\* 1-7, Sunday is 1 \*/  

   int hour;       /\* 0-23 \*/  

   int minute;     /\* 0-59 \*/  

   int second;     /\* 0-59 \*/  

   int hundredth;  /\* 0-99 \*/  

   int dst;        /\* FALSE or TRUE \*/  

   int zone;       /\* -11 to +11 \*/  

   TIMEDATE GM;  

} TIME;


 


**Description :**



This is the
Domino expanded components of a time/date. This structure is used with the
TimeGMToLocal and TimeLocalToGM functions.  In addition, the ".GM"
member can be altered using any other C API time/date function that manipulates
a TIMEDATE structure.


 **See Also :**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[TimeDateIncrement](TimeDateIncrement.md)**


**[TimeDateAdjust](TimeDateAdjust.md)**


**[TimeGMToLocal](TimeGMToLocal.md)**


**[TimeLocalToGM](TimeLocalToGM.md)**



----------------------------------------------------------------------------------------------------------


 





