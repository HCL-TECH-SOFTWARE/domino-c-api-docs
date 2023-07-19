##### Data Type : Views
##### VIEW_CALENDAR_FORMAT2 - Secondary calendar view format descriptor.
---
```
#include <viewfmt.h>
```

**Definition :**

typedef struct {
   WORD Signature;               /* VIEW_CALENDAR_FORMAT2_SIGNATURE
                                 /* Attributes initialized when
                                    MinorVersion = 1 */
   COLOR_VALUE DayDateBkColor;   /* Color for day/date background
                                    area */
   COLOR_VALUE NonMonthBkColor;  /* Color for non-month date
                                    background area */
   COLOR_VALUE NonMonthTextColor;/* Color for non-month font */
	COLOR_VALUE DayDateColor; /* V6 - Day and Date display */
	COLOR_VALUE TimeSlotColor; /* V6 - Time Slot display */
	COLOR_VALUE HeaderColor; /* V6 - Month Headers */
	COLOR_VALUE TodayRGBColor; /* V6 - Today color */
	FONTID WeekDayMonthFont; /* One week view - Day and Month display */
	DWORD  Spare[3];
} VIEW_CALENDAR_FORMAT2;

**Description :**

This structure describes the secondary format of a calendar-style view for Domino and Notes R5 and later.


**See Also :**
[VIEW_CALENDAR_FORMAT2_SIGNATURE](/domino-c-api-docs/reference/Symb/VIEW_CALENDAR_FORMAT2_SIGNATURE)
---
