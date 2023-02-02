##### Function : Time
##### TimeExtractTicks - Extracts the number of ticks since GMT midnight from a TIMEDATE value.
---
##### #include <misc.h>
DWORD LNPUBLIC **TimeExtractTicks(**

	const TIMEDATE far *Time);
**Description :**
This function extracts the number of ticks since GMT midnight from a TIMEDATE 
value.  There are 100 ticks in one second.
**Parameters :**
Input :
Time  -  Pointer to TIMEDATE value to extract.

Output :
(routine)  -  Extracted number of ticks since GMT midnight.


**See Also :**
[TimeConstruct](D:/md_files/TimeConstruct.md)
---
