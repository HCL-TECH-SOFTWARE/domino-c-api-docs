##### Function : Time
##### TimeExtractDate - Extracts the Julian date, including zone information, from a TIMEDATE value.
---
```
#include <misc.h>
DWORD LNPUBLIC TimeExtractDate(

	const TIMEDATE far *Time);
```
**Description :**

This function extracts the Julian date, including zone information, from a 
TIMEDATE value.

**Parameters :**
Input :
Time  -  Pointer to the TIMEDATE value to extract.

Output :
(routine)  -  Extracted Julian Date including zone information.



**See Also :**
[TimeConstruct](/reference/Func/TimeConstruct)
---
