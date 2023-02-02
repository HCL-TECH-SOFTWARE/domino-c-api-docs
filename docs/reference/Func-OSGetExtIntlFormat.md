##### Function : Time
##### OSGetExtIntlFormat - Get international format extended.
---
##### #include <intl.h>
WORD LNPUBLIC **OSGetExtIntlFormat(**

	char  item,
	char  index,
	void *buff,
	WORD  bufSize);
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
[ABBRERANAME](D:/md_files/ABBRERANAME.md)
[ABBR_MONTH_NAMES](D:/md_files/ABBR_MONTH_NAMES.md)
[ABBR_WEEKDAY_NAMES](D:/md_files/ABBR_WEEKDAY_NAMES.md)
[CALENDARTYPE](D:/md_files/CALENDARTYPE.md)
[CALENDAR_xxx](D:/md_files/CALENDAR_xxx.md)
[ERANAME](D:/md_files/ERANAME.md)
[EXT_xxx](D:/md_files/EXT_xxx.md)
[MONTH_NAMES](D:/md_files/MONTH_NAMES.md)
[WEEKDAY_NAMES](D:/md_files/WEEKDAY_NAMES.md)
---
