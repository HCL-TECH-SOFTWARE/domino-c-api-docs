##### Function : Time
##### TimeDateEqual - Returns whether two TIMEDATE values are equal.
---
```
#include <misc.h>
BOOL TimeDateEqual(

	TIMEDATE far *t1,
	TIMEDATE far *t2);
```
**Description :**

This is a macro which returns TRUE if two TIMEDATE values are equal and FALSE 
if otherwise.  The time zone components are ignored.

**Parameters :**
Input :
t1  -  A pointer to a TIMEDATE structure containing the first binary value.

t2  -  A pointer to a TIMEDATE structure containing the second binary value .

Output :
(routine)  -  TRUE if the TIMEDATE values are the same (the time zone components are ignored), otherwise FALSE



**See Also :**
[TIMEDATE](/reference/Data/TIMEDATE)
[TimeDateCollate](/reference/Func/TimeDateCollate)
[TimeDateCompare](/reference/Func/TimeDateCompare)
[TimeDateDifference](/reference/Func/TimeDateDifference)
---
