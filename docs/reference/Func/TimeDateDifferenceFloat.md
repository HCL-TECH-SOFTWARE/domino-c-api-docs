##### Function : Time
##### TimeDateDifferenceFloat - Floating-point difference between two TIMEDATE values.
---
```
#include <misc.h>
void LNPUBLIC TimeDateDifferenceFloat(

	const TIMEDATE far *t1,
	const TIMEDATE far *t2,
	NUMBER far *difference);
```
**Description :**

This function returns a double value containing the difference in seconds 
between two TIMEDATE values.  The values are normalized to a common time zone 
for the calculation.  If the first argument is greater than the second, the 
returned value is positive.  If the first argument is smaller than the second, 
the returned value is negative.  

**Parameters :**
Input :
t1  -  A pointer to a TIMEDATE structure containing the first binary value.

t2  -  A pointer to a TIMEDATE structure containing the second binary value.

Output :
difference  -  Address where the floating-point result is to be stored.  The difference is in seconds.


**Sample Usage :**
```

   /* Obtain the difference in SECONDS between two TIMEDATEs       */

   NUMBER time_delta;

   TimeDateDifferenceFloat(&binary_td2,&binary_td1, &time_delta);   

```
**See Also :**
[TimeDateAdjust](/domino-c-api-docs/reference/Func/TimeDateAdjust)
[TimeDateCompare](/domino-c-api-docs/reference/Func/TimeDateCompare)
[TimeDateDifference](/domino-c-api-docs/reference/Func/TimeDateDifference)
[TimeDateIncrement](/domino-c-api-docs/reference/Func/TimeDateIncrement)
---
