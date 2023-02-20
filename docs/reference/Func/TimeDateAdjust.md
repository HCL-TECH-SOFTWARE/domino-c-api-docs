##### Function : Time
##### TimeDateAdjust - Change the time and/or date of a binary TIMEDATE.
---
```
#include <misc.h>
BOOL LNPUBLIC TimeDateAdjust(

	TIMEDATE far *Time,
	int  seconds,
	int  minutes,
	int  hours,
	int  days,
	int  months,
	int  years);
```
**Description :**

This function adjusts the binary representation of TIMEDATE structure members, 
using the adjustment values supplied in any combination of  seconds, minutes, 
hours, days, months, and years values. Any adjustment can carry over to the 
next unit, i.e., minutes_delta = 65; results in a positive adjustment of 1 hour 
and 5 minutes.  The time zone value and daylight savings time state are not 
affected by these adjustments, therefore it is possible to manipulate TIMEDATE 
values derived from many different time zones.

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

seconds  -  Number of seconds to add to or subtract from the binary TIMEDATE. A value >= the minimum (int) value and <= the maximum (int) value for the host OS and hardware. Zero (0) indicates no change.

minutes  -  Number of minutes to add to or subtract from the binary TIMEDATE. A value >= the minimum (int) value and <= the maximum (int) value for the host OS and hardware. Zero (0) indicates no change.

hours  -  Number of hours to add to or subtract from the binary TIMEDATE. A value >= the minimum (int) value and <= the maximum (int) value for the host OS and hardware. Zero (0) indicates no change.

days  -  Number of days to add to or subtract from the binary TIMEDATE. A value >= the minimum (int) value and <= the maximum (int) value for the host OS and hardware. Zero (0) indicates no change.

months  -  Number of months to add to or subtract from the binary TIMEDATE. A value >= the minimum (int) value and <= the maximum (int) value for the host OS and hardware. Zero (0) indicates no change.

years  -  Number of years to add to or subtract from the binary TIMEDATE. A value >= the minimum (int) value and <= the maximum (int) value for the host OS and hardware. Zero (0) indicates no change.

Output :
(routine)  -  FALSE if adjustment was successful, TRUE if adjustment failed.


Time  -  The address of the TIMEDATE structure in which the adjusted binary value is returned.


**Sample Usage :**
```

   /* Adjust all components of TIMEDATE */

   seconds_delta = +61;      /* bump the time */
   minutes_delta = +61;
   hours_delta   = +25;
   days_delta    = +31;      /* bump the date */
   months_delta  = +13;
   years_delta   = -1;
   if (TimeDateAdjust(&binary_td1, seconds_delta,
                      minutes_delta, hours_delta,
                      days_delta, months_delta,
                      years_delta))
       goto Exit;

```
**See Also :**
[OSCurrentTIMEDATE](/reference/Func/OSCurrentTIMEDATE)
---
