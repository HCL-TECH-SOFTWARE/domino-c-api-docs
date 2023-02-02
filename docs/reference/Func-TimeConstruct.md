##### Function : Time
##### TimeConstruct - Constructs a TIMEDATE from its two components.
---
##### #include <misc.h>
void LNPUBLIC **TimeConstruct(**

	DWORD  Date,
	DWORD  Time,
	TIMEDATE far *result);
**Description :**
This function constructs a TIMEDATE from its two components (date and ticks 
since midnight) with no time zone information.
**Parameters :**
Input :
Date  -  Julian date.

Time  -  Number of ticks since midnight.

Output :
(routine)  -  None


result  -  Pointer to the returned TIMEDATE value.

**See Also :**
[TimeExtractJulianDate](D:/md_files/TimeExtractJulianDate.md)
[TimeExtractDate](D:/md_files/TimeExtractDate.md)
---
