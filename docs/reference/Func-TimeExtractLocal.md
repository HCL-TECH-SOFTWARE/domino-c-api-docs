##### Function : Time
##### TimeExtractLocal - Converts a TIMEDATE value to just a time or a date.
---
##### #include <misc.h>
void LNPUBLIC **TimeExtractLocal(**

	const TIMEDATE far *Time,
	BOOL  fTime,
	TIMEDATE far *retTime);
**Description :**
This function converts a TIMEDATE value to just a time or date in the local 
time zone, even if one of the components happens to be a wildcard (ANYDAY or 
ALLDAY).
**Parameters :**
Input :
Time  -  Pointer to TIMEDATE value to be extracted.

fTime  -  Use TRUE to extract the time, FALSE to extract the date.

Output :
(routine)  -  None


retTime  -  Extracted TIMEDATE value.

**See Also :**
[TIMEDATE](D:/md_files/TIMEDATE.md)
---
