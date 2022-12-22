




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



**TIMEDATE** **-** Domino
binary time/date format.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



typedef struct
tagTIMEDATE {  

   DWORD Innards[2];  

} TIMEDATE;


 


**Description :**



This is the
Domino binary time/date format. This structure only should be interpreted using
the C API time/date calls -- it cannot easily be parsed directly.


 


All
TIMEDATEs are stored in GMT. If you need to take a TIMEDATE and store it as a
GMT time in TIME format, do the following:


- Define a
variable of type TIME.


- Copy the
TIMEDATE you wish to extract to the .GM member of the TIME structure.


- Set the
.zone and .dst members of the TIME structure to zero. This indicates that you
want the time stored as Greenwich Mean Time, without Daylight Savings Time.


- Call the
function TimeGMToLocalZone(), passing it a pointer to the TIME structure you've
defined. This function will fill in the remaining integer members of the TIME
structure with the time in GMT.


 **See Also :**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[TimeGMToLocalZone](TimeGMToLocalZone.md)**



----------------------------------------------------------------------------------------------------------


 





