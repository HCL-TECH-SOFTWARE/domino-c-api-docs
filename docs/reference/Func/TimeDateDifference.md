##### Function : Time
##### TimeDateDifference - Difference between two TIMEDATE values.
---
```
#include <misc.h>
LONG LNPUBLIC TimeDateDifference(

	const TIMEDATE far *t1,
	const TIMEDATE far *t2);
```
**Description :**

This function returns a long integer value containing the difference in seconds 
between two TIMEDATE values.  The values are normalized to a common time zone 
for the calculation.  If the first argument is greater than the second, the 
returned value is a positive LONG.  If the first argument is smaller than the 
second, the returned value is a negative LONG.

**Parameters :**
Input :
t1  -  A pointer to a TIMEDATE structure containing the first binary value.

t2  -  A pointer to a TIMEDATE structure containing the second binary value.

Output :
(routine)  -  Returns a LONG containing the diffence in seconds.



**Sample Usage :**
```

   /* Obtain the difference in SECONDS between two TIMEDATEs       */

   time_delta = TimeDateDifference(&binary_td2,&binary_td1);   

```
**See Also :**
[TimeDateAdjust](/domino-c-api-docs/reference/Func/TimeDateAdjust)
[TimeDateCompare](/domino-c-api-docs/reference/Func/TimeDateCompare)
[TimeDateDifferenceFloat](/domino-c-api-docs/reference/Func/TimeDateDifferenceFloat)
[TimeDateIncrement](/domino-c-api-docs/reference/Func/TimeDateIncrement)
[TimeDateEqual](/domino-c-api-docs/reference/Func/TimeDateEqual)
[TimeDateCollate](/domino-c-api-docs/reference/Func/TimeDateCollate)
---
