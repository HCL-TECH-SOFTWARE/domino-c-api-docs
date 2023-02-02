##### Function : Time
##### TimeDateCompare - Compares two binary TIMEDATE values.
---
##### #include <misc.h>
int LNPUBLIC **TimeDateCompare(**

	const TIMEDATE far *t1,
	const TIMEDATE far *t2);
**Description :**
This function normalizes each argument to the same time zone, and compares the 
two binary TIMEDATE values and returns an integer result.
**Parameters :**
Input :
t1  -  A pointer to a TIMEDATE structure containing the first binary value.

t2  -  A pointer to a TIMEDATE structure containing the second binary value.

Output :
(routine)  -  Returns -1 if the first argument is less than second one, Zero (0) if the first and second arguments are equal, and +1 if the first argument is greater than the second one.


**Sample Usage :**
```
   
   td_compare_result = TimeDateCompare(&binary_td2,&binary_td3);

```
**See Also :**
[OSCurrentTIMEDATE](D:/md_files/OSCurrentTIMEDATE.md)
[TimeDateCollate](D:/md_files/TimeDateCollate.md)
[TimeDateEqual](D:/md_files/TimeDateEqual.md)
[TimeDateDifference](D:/md_files/TimeDateDifference.md)
[TIMEDATE](D:/md_files/TIMEDATE.md)
---
