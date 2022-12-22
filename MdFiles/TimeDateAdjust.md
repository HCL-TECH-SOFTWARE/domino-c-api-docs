




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




 


**Function : Time**



**TimeDateAdjust** **- Change
the time and/or date of a binary TIMEDATE.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



BOOL
LNPUBLIC **TimeDateAdjust(**  

      TIMEDATE far \*Time,  

      int  seconds,  

      int  minutes,  

      int  hours,  

      int  days,  

      int  months,  

      int  years**);**



**Description :**



This
function adjusts the binary representation of TIMEDATE structure members, using
the adjustment values supplied in any combination of  seconds, minutes, hours,
days, months, and years values. Any adjustment can carry over to the next unit,
i.e., minutes\_delta = 65; results in a positive adjustment of 1 hour and 5
minutes.  The time zone value and daylight savings time state are not affected
by these adjustments, therefore it is possible to manipulate TIMEDATE values
derived from many different time zones.  

  

Adjustments are performed in order from smallest (seconds) to largest (years); 
this order may affect the results when, for example, adjusting both days and
months since different months have different numbers of days.  For example,
subtracting 7 days and 1 month from 11/3/94 will result in the date 9/27/94. 
If another order is desired, such as subtracting the month first,
TimeDateAdjust can be called first to subtract 1 month, then called again to
subtract 7 days, resulting in the date 9/26/94.


 


**Parameters :**



Input :  

Time  -  The address of the TIMEDATE structure to be adjusted.  

  

seconds  -  Number of seconds to add to or subtract from the binary TIMEDATE. A
value >= the minimum (int) value and <= the maximum (int) value for the host
OS and hardware. Zero (0) indicates no change.  

  

minutes  -  Number of minutes to add to or subtract from the binary TIMEDATE. A
value >= the minimum (int) value and <= the maximum (int) value for the
host OS and hardware. Zero (0) indicates no change.  

  

hours  -  Number of hours to add to or subtract from the binary TIMEDATE. A
value >= the minimum (int) value and <= the maximum (int) value for the
host OS and hardware. Zero (0) indicates no change.  

  

days  -  Number of days to add to or subtract from the binary TIMEDATE. A value
>= the minimum (int) value and <= the maximum (int) value for the host OS
and hardware. Zero (0) indicates no change.  

  

months  -  Number of months to add to or subtract from the binary TIMEDATE. A
value >= the minimum (int) value and <= the maximum (int) value for the
host OS and hardware. Zero (0) indicates no change.  

  

years  -  Number of years to add to or subtract from the binary TIMEDATE. A
value >= the minimum (int) value and <= the maximum (int) value for the
host OS and hardware. Zero (0) indicates no change.  

  




Output :  

(routine)  -  FALSE if adjustment was successful, TRUE if adjustment failed.  

  

  

Time  -  The address of the TIMEDATE structure in which the adjusted binary
value is returned.  

  




 **Sample Usage :**


  

   /\* Adjust all components of TIMEDATE \*/  

  

   seconds\_delta = +61;      /\* bump the time \*/  

   minutes\_delta = +61;  

   hours\_delta   = +25;  

   days\_delta    = +31;      /\* bump the date \*/  

   months\_delta  = +13;  

   years\_delta   = -1;  

   if (TimeDateAdjust(&binary\_td1, seconds\_delta,  

                      minutes\_delta, hours\_delta,  

                      days\_delta, months\_delta,  

                      years\_delta))  

       goto Exit;  

  




 **See Also :**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





