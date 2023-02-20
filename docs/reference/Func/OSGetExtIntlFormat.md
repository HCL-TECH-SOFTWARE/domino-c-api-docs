##### Function : Time
##### OSGetExtIntlFormat - Get international format extended.
---
```
#include <intl.h>
WORD LNPUBLIC OSGetExtIntlFormat(

	char  item,
	char  index,
	void *buff,
	WORD  bufSize);
```
**Description :**

This function will retrieve the international format of various operating 
system time and date attributes.

**Parameters :**
Input :
item  -  The item you want to retrieve.  See: ABBRERANAME, ABBR_MONTH_NAMES, ABBR_WEEKDAY_NAMES, CALENDARTYPE, CALENDAR_xxx, ERANAME, EXT_xxx, MONTH_NAMES, WEEKDAY_NAMES.

index  -  Index for month (1-12) or weekday (1-7) names.

bufSize  -  Size of output buffer

Output :
(routine)  -  Ouput string length.


buff  -  Output buffer.


**See Also :**
[ABBRERANAME](/reference/Symb/ABBRERANAME)
[ABBR_MONTH_NAMES](/reference/Symb/ABBR_MONTH_NAMES)
[ABBR_WEEKDAY_NAMES](/reference/Symb/ABBR_WEEKDAY_NAMES)
[CALENDARTYPE](/reference/Symb/CALENDARTYPE)
[CALENDAR_xxx](/reference/Symb/CALENDAR_xxx)
[ERANAME](/reference/Symb/ERANAME)
[EXT_xxx](/reference/Symb/EXT_xxx)
[MONTH_NAMES](/reference/Symb/MONTH_NAMES)
[WEEKDAY_NAMES](/reference/Symb/WEEKDAY_NAMES)
---
