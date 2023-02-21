##### Function : Time
##### TimeLocalToGM - Uses integer members of TIME to create TIMEDATE.
---
```
#include <misc.h>
BOOL LNPUBLIC TimeLocalToGM(

	TIME far *Time);
```
**Description :**

This function takes the integer members of a TIME structure: seconds, minutes, 
hours, days, months, years, zone, and dst (Daylight Savings Time), and stores 
the binary equivalent in the TIMEDATE member.  

It is useful in bridging from data structures required by Operating Systems or 
'C' library time/date functions or in the process of converting a TIMEDATE 
value from one time zone to its equivalent value in an other time zone.

**Parameters :**
Input :
Time  -  A pointer to a TIME structure whose members: Time->seconds, Time->minutes, Time->hours, Time->days, Time->months, Time->years, Time->zone, and Time->dst members contain the appropriate integer values for a particular time/date.

Output :
(routine)  -  Returns FALSE if successful and TRUE if not.


Time  -  The address of a TIME structure whose Time->GM member now contains the returned binary TIMEDATE value. 


**Sample Usage :**
```
/* Adjust for GMT to local conversion and then Condense */
/* individual SEQNUM time struct members to GM member.  */

if (zone_num > 0)
{
   hours_delta = (zone_num - ((dst_status)? 1: 0));
   days_delta  = 0;
}
else if(zone_num < 0)
{
   hours_delta = -(zone_num - ((dst_status)? 1: 0));
   days_delta  = 1;
}
time_seqnum.hour -= hours_delta;
time_seqnum.day  -= days_delta;
time_seqnum.zone  = zone_num;
time_seqnum.dst   = dst_status;
if (TimeLocalToGM(&time_seqnum))
   goto Exit;
```
**See Also :**
[TimeGMToLocal](/domino-c-api-docs/reference/Func/TimeGMToLocal)
[TimeGMToLocalZone](/domino-c-api-docs/reference/Func/TimeGMToLocalZone)
[OSCurrentTimeZone](/domino-c-api-docs/reference/Func/OSCurrentTimeZone)
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
---
