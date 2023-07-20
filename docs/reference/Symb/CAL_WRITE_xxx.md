##### Symbolic Value : iCalendar
##### CAL_WRITE_xxx - Flags that control behavior of the calendar APIs - Used when APIS take iCalendar input to modify calendar data
---
```
#include <calapi.h>
```

**Symbolic Values :**

	CAL_WRITE_COMPLETE_REPLACE	  -  Used when APIs modify entry data via CalUpdateEntry.
This flag means that NO data is preserved from the original entry and the resulting entry is 100% a product of the iCalendar passed in.
NOTE: When this flag is NOT used, some content may be preserved during an update if that particular content was not included in the iCalendar input.
This includes:Body,Attachments,Custom data properties as specified in $CSCopyItems

	CAL_WRITE_DISABLE_IMPLICIT_SCHEDULING	  -  Used when APIs create or modify calendar entries where the organizer is the mailfile owner.
When a calendar entry is modified with CAL_WRITE_DISABLE_IMPLICIT_SCHEDULING set, no notices are sent (invites, updates, reschedules, cancels, etc)
Note: This is not intended for cases where you are saving a meeting as a draft (since there is currently not a capability to then send it later. It will also not allow some notices to go out but other notices not to go out (such as, send invites to added invitees but dont send updates to existing invitees).
Rather, this is targeted at callers that prefer to be responsible for sending out notices themselves through a separate mechanism.

	CAL_WRITE_IGNORE_VERIFY_DB	  -  Used when APIs create or modify entries on the calendar
This will allow creation/modification of calendar entries, even if the database is not a mailfile

	CAL_WRITE_USE_ALARM_DEFAULTS	  -  By default, alarms will be created on calendar entries based on VALARM content of iCalendar input. Use of this flag will disregard VALARM information in the iCalendar and use the user's default alarm settings for created or updated entries.


**Description :**




**See Also :**
---
