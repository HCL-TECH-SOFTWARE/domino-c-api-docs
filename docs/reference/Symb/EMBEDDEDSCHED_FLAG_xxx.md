##### Symbolic Value : Constants
##### EMBEDDEDSCHED_FLAG_xxx - Flags for CDEMBEDDEDSCHEDCTL.
---
```
#include <editods.h>
```

**Symbolic Values :**

	EMBEDDEDSCHED_FLAG_USE_COLORS1	  -  If flag is set, color values for BusyTimeColor, FreeTimeColor, NoData Color, DataRestrictedColor and GridLineColor contain valid information. Default color values are used if this flag is not set.

	EMBEDDEDSCHED_FLAG_NO_INITFROMITEMS	  -  If flag is set, scheduler info (participants, appointment start/end time, etc.) is not initialized from item values on the note.

	EMBEDDEDSCHED_FLAG_NO_REFRESHFROMITEMS	  -  If flag is set, scheduler info is not refreshed from item values on the note when document is recalculated.

	EMBEDDEDSCHED_FLAG_ALLOW_FILTERING	  -  If flag is set, allow filtering.

	EMBEDDEDSCHED_FLAG_USE_COLORS2	  -  Reserved for future use.

	EMBEDDEDSCHED_FLAG_NO_SHOWLEGEND	  -  If flag is set, color legend is not shown.

	EMBEDDEDSCHED_FLAG_SHOWINTERVALINDICATOR	  -  If flag is set, appointment interval indicator is shown.

	EMBEDDEDSCHED_FLAG_SHOW_TWISTIES	  -  If flag is set, twisties are shown.

	EMBEDDEDSCHED_FLAG_ALLOW_EDIT_INPLACE	  -  If flag is set, scheduler can be edited in place.

	EMBEDDEDSCHED_FLAG_ATTENDEE_WIDTH_DEFINED	  -  If flag is set, overall width of the scheduler is defined.

	EMBEDDEDSCHED_FLAG_ATTENDEE_WIDTH_FIXED	  -  If flag is set, width of the left side of the control where attendee names are displayed is fixed.

	EMBEDDEDSCHED_FLAG_PEOPLE_INVISIBLE	  -  If flag is set, "people" (or "top") area is not visible in the scheduler.

	EMBEDDEDSCHED_FLAG_ROOMS_VISIBLE	  -  If flag is set, "rooms" (or "middle") area is visible in the scheduler.

	EMBEDDEDSCHED_FLAG_RESOURCES_VISIBLE	  -  If flag is set, "resources" (or "bottom") area is visible in the scheduler.

	EMBEDDEDSCHED_FLAG_PEOPLE_FIXEDHEIGHT	  -  If flag is set, "people" (or "top") area is a fixed height in the scheduler.

	EMBEDDEDSCHED_FLAG_ROOMS_FIXEDHEIGHT	  -  If flag is set, "rooms" (or "middle") area is a fixed height in the scheduler.

	EMBEDDEDSCHED_FLAG_RESOURCES_FIXEDHEIGHT	  -  If flag is set, "resources" (or "bottom") area is a fixed height in the scheduler.

	EMBEDDEDSCHED_FLAG_ATTENDEE_LINES_DEFINED	  -  If flag is set, PeopleLines, RoomsLines and ResourcesLines values in CDEMBEDDEDSCHEDCTL contain valid data.

	EMBEDDEDSCHED_FLAG_RTL_READING	  -  If flag is set, display schedule from right to left.

	EMBEDDEDSCHED_FLAG_NO_LAUNCH	  -  If flag is set, don't launch scheduler.


**Description :**

Flags for CDEMBEDDEDSCHEDCTL.


**See Also :**
[CDEMBEDDEDSCHEDCTL](/domino-c-api-docs/reference/Data/CDEMBEDDEDSCHEDCTL)
[CDPLACEHOLDER](/domino-c-api-docs/reference/Data/CDPLACEHOLDER)
---
