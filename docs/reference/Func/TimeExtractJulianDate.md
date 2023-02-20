##### Function : Time
##### TimeExtractJulianDate - Extracts the Julian date from a TIMEDATE value.
---
```
#include <misc.h>
DWORD LNPUBLIC TimeExtractJulianDate(

	const TIMEDATE far *Time);
```
**Description :**

This function extracts the Julian date from a TIMEDATE value, trimming off the 
time zone information.

**Parameters :**
Input :
Time  -  Pointer to the TIMEDATE value to extract.

Output :
(routine)  -  Extracted Julian Date



**See Also :**
[TimeConstruct](/reference/Func/TimeConstruct)
---
