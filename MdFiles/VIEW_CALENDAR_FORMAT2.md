




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



**Data Type : Views**



**VIEW\_CALENDAR\_FORMAT2** **-** Secondary
calendar view format descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct {  

   WORD Signature;               /\* VIEW\_CALENDAR\_FORMAT2\_SIGNATURE


                         
       /\* Attributes initialized when


                                   
MinorVersion = 1 \*/  

   COLOR\_VALUE DayDateBkColor;   /\* Color for day/date background


                                   
area \*/


   COLOR\_VALUE
NonMonthBkColor;  /\* Color for non-month date


                                   
background area \*/


   COLOR\_VALUE
NonMonthTextColor;/\* Color for non-month font \*/


        COLOR\_VALUE    DayDateColor;  /\*
V6 - Day and Date display \*/


        COLOR\_VALUE    TimeSlotColor; /\*
V6 - Time Slot display \*/


        COLOR\_VALUE    HeaderColor;   /\*
V6 - Month Headers \*/


        COLOR\_VALUE
TodayRGBColor;    /\* V6 - Today color \*/


        FONTID  WeekDayMonthFont;      /\*
One week view - Day and Month display \*/


        DWORD          Spare[3];  

} VIEW\_CALENDAR\_FORMAT2;


 


**Description :**



This
structure describes the secondary format of a calendar-style view for Domino
and Notes R5 and later.


 **See Also :**


**[VIEW\_CALENDAR\_FORMAT2\_SIGNATURE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/41B4927C140C0B518525667800742B41)**



----------------------------------------------------------------------------------------------------------


 





