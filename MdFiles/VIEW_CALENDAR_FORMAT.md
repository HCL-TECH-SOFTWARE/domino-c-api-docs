




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




**Initial Release 4.5**



**Data Type : Views**



**VIEW\_CALENDAR\_FORMAT** **-** Calendar
view format descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct


    {


    BYTE    Version;                              /\*
Version Number \*/   


    BYTE    Formats;                              /\*
Formats supported by this view VIEW\_CAL\_FORMAT\_XXX.\*/


    FONTID  DayDateFont;           /\*
Day and Date display \*/


    FONTID  TimeSlotFont;          /\*
Time Slot display \*/


    FONTID  HeaderFont;              
     /\* Month Headers \*/


 


    WORD    DaySeparatorsColor;           /\*
Lines separating days \*/


    WORD    TodayColor;                   /\*
Color Today is displayed in \*/


 


    WORD    wFlags;                       /\*
Misc Flags - CAL\_xxx \*/


    


    WORD    BusyColor;                    /\*
Color busy times are displayed in \*/


 


    WORD   
wTimeSlotStart;                      /\* TimeSlot start time (in minutes from
midnight) \*/


    WORD    wTimeSlotEnd;                 /\*
TimeSlot end time (in minutes from midnight) \*/


    WORD   
wTimeSlotDuration;            /\* TimeSlot duration (in minutes) \*/


 


    COLOR\_VALUE
DaySeparatorsColorExt;    /\* written by v5; Same as DaySeparatorsColor, but can
be any color \*/


    COLOR\_VALUE
BusyColorExt;             /\* written by v5; Same as BusyColor, but can be any
color \*/


 


    BYTE    MinorVersion;                 /\*
Minor version-VIEW\_CAL\_FORMAT\_MINOR\_xxx \*/


    BYTE    InitialFormat;                /\*
Initial format to display.  0=last viewed by user \*/


    


    DWORD   CalGridBkColor;                       /\*
Background color of Calendar Grid \*/


    DWORD   WorkHoursColor;                       /\*
Background color for the work hours in the calendar grid \*/ 


    DWORD   ToDoBkColor;                  /\*
Background color for the ToDo entry region \*/


    DWORD   HeaderBkColor;                /\*
Background color for calendar view's header background \*/


 


    }
VIEW\_CALENDAR\_FORMAT;


 


**Description :**



This
structure describes the format of a calendar-style view.


 **See Also :**


**[CAL\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DAE109DE9179EE568525636100767692)**


**[VIEW\_CALENDAR\_FORMAT\_VERSION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/084DE46501310F5F852563610075767F)**


**[VIEW\_CAL\_FORMAT\_MINOR\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DF129000AC532F3B852566780073BD75)**


**[VIEW\_CAL\_FORMAT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CBEA16AD260C50DE8525636100758FF5)**



----------------------------------------------------------------------------------------------------------


 





