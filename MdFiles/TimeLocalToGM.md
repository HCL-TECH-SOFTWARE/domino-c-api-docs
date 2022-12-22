




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



**TimeLocalToGM** **- Uses
integer members of TIME to create TIMEDATE.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



BOOL
LNPUBLIC **TimeLocalToGM(**  

      TIME far \*Time**);**



**Description :**



This
function takes the integer members of a TIME structure: seconds, minutes,
hours, days, months, years, zone, and dst (Daylight Savings Time), and stores
the binary equivalent in the TIMEDATE member.    

  

It is useful in bridging from data structures required by Operating Systems or
'C' library time/date functions or in the process of converting a TIMEDATE
value from one time zone to its equivalent value in an other time zone.


 


**Parameters :**



Input :  

Time  -  A pointer to a TIME structure whose members: Time->seconds,
Time->minutes, Time->hours, Time->days, Time->months,
Time->years, Time->zone, and Time->dst members contain the appropriate
integer values for a particular time/date.  

  




Output :  

(routine)  -  Returns FALSE if successful and TRUE if not.  

  

  

Time  -  The address of a TIME structure whose Time->GM member now contains
the returned binary TIMEDATE value.   

  




 **Sample Usage :**


/\* Adjust for GMT to
local conversion and then Condense \*/  

/\* individual SEQNUM time struct members to GM member.  \*/  

  

if (zone\_num > 0)  

{  

   hours\_delta = (zone\_num - ((dst\_status)? 1: 0));  

   days\_delta  = 0;  

}  

else if(zone\_num < 0)  

{  

   hours\_delta = -(zone\_num - ((dst\_status)? 1: 0));  

   days\_delta  = 1;  

}  

time\_seqnum.hour -= hours\_delta;  

time\_seqnum.day  -= days\_delta;  

time\_seqnum.zone  = zone\_num;  

time\_seqnum.dst   = dst\_status;  

if (TimeLocalToGM(&time\_seqnum))  

   goto Exit;


 **See Also :**


**[TimeGMToLocal](TimeGMToLocal.md)**


**[TimeGMToLocalZone](TimeGMToLocalZone.md)**


**[OSCurrentTimeZone](OSCurrentTimeZone.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





