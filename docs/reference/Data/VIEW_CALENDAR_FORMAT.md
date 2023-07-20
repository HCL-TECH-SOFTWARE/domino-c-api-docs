##### Data Type : Views
##### VIEW_CALENDAR_FORMAT - Calendar view format descriptor.
---
```
#include <viewfmt.h>
```

**Definition :**
```
typedef struct
	{
	BYTE Version;    /* Version Number */ 
	BYTE Formats;    /* Formats supported by this view 
VIEW_CAL_FORMAT_XXX.*/
	FONTID DayDateFont;  /* Day and Date display */
	FONTID TimeSlotFont;  /* Time Slot display */
	FONTID HeaderFont;      /* Month Headers */

	WORD DaySeparatorsColor;  /* Lines separating days */
	WORD    TodayColor;   /* Color Today is displayed in */

	WORD wFlags;    /* Misc Flags - CAL_xxx */
	
	WORD    BusyColor;   /* Color busy times are displayed in */

	WORD    wTimeSlotStart;   /* TimeSlot start time (in minutes from 
midnight) */
	WORD    wTimeSlotEnd;   /* TimeSlot end time (in minutes from midnight) 
*/
	WORD    wTimeSlotDuration;  /* TimeSlot duration (in minutes) */

	COLOR_VALUE DaySeparatorsColorExt; /* written by v5; Same as 
DaySeparatorsColor, but can be any color */
	COLOR_VALUE BusyColorExt;  /* written by v5; Same as BusyColor, but can 
be any color */

	BYTE MinorVersion;   /* Minor version-VIEW_CAL_FORMAT_MINOR_xxx */
	BYTE InitialFormat;   /* Initial format to display.  0=last viewed by 
user */
	
	DWORD CalGridBkColor;   /* Background color of Calendar Grid */
	DWORD WorkHoursColor;   /* Background color for the work hours in the 
calendar grid */ 
	DWORD ToDoBkColor;   /* Background color for the ToDo entry region */
	DWORD HeaderBkColor;   /* Background color for calendar view's header 
background */

	} VIEW_CALENDAR_FORMAT;
```

**Description :**

This structure describes the format of a calendar-style view.


**See Also :**
[CAL_xxx](/domino-c-api-docs/reference/Symb/CAL_xxx)
[VIEW_CALENDAR_FORMAT_VERSION](/domino-c-api-docs/reference/Symb/VIEW_CALENDAR_FORMAT_VERSION)
[VIEW_CAL_FORMAT_MINOR_xxx](/domino-c-api-docs/reference/Symb/VIEW_CAL_FORMAT_MINOR_xxx)
[VIEW_CAL_FORMAT_xxx](/domino-c-api-docs/reference/Symb/VIEW_CAL_FORMAT_xxx)
---
