##### Function : Time
##### TimeDateCollate - Compares two binary TIMEDATE values.
---
```
#include <misc.h>
int LNPUBLIC TimeDateCollate(

	const TIMEDATE far *t1,
	const TIMEDATE far *t2);
```
**Description :**

This function is similar to TimeDateCompare.  It compares two binary TIMEDATE 
values and returns an integer result, but without regard to their time zone 
components.  Generally, unlike TimeDateCompare,  it will not work for wildcards 
(either of the dates is ANYDAY or if either of the times is ALLDAY).  It will 
work however for equality even if wildcards are present.  This routine is 
faster than TimeDateCompare

**Parameters :**
Input :
t1  -   A pointer to a TIMEDATE structure containing the first binary value.

t2  -  A pointer to a TIMEDATE structure containing the second binary value.

Output :
(routine)  -  Returns -1 if the first argument is less than second one, Zero (0) if the first and second arguments are equal, and +1 if the first argument is greater than the second one.



**See Also :**
[TimeDateCompare](/reference/Func/TimeDateCompare)
[TIMEDATE](/reference/Data/TIMEDATE)
[TimeDateDifference](/reference/Func/TimeDateDifference)
[TimeDateEqual](/reference/Func/TimeDateEqual)
[OSCurrentTIMEDATE](/reference/Func/OSCurrentTIMEDATE)
---
