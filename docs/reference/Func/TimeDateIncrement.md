##### Function : Time
##### TimeDateIncrement - Increment binary TIMEDATE value.
---
```
#include <misc.h>
STATUS LNPUBLIC TimeDateIncrement(

	TIMEDATE far *Time,
	LONG  Interval);
```
**Description :**

This function increments the contents of a TIMEDATE structure using the 
specified increment.  The value of the increment is taken as being in 10 
millisecond units.

**Parameters :**
Input :
Time  -  A pointer to a TIMEDATE structure containing the Time/Date you wish to increment.

Interval  -  LONG containing positive increment in 10 millisecond units.  100L = 1 sec, 1000L = 10 sec, and 6000L = 1 minute.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include: 

NOERROR - Incrementing operation was successful .
ERR_TREQ - TIME must be specified, not just DATE.  The TIMEDATE stucture provided was set to the TIMEDATE_WILDCARD (more specifically, the Innards[0] member of this structure was set to ALLDAY, which is usually used as a wild-card in database operations).


Time  -  The address of  the TIMEDATE structure in which the original value, plus the increment is returned.


**Sample Usage :**
```

   /* Increment the copy by a given interval in (10ms units)       */

   time_increment = 6000L;       /* increment TimeDate by 60 secs  */
   if (error_status = TimeDateIncrement(&binary_td2, time_increment))
       goto Exit;


```
**See Also :**
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
---
