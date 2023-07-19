##### Symbolic Value : iCalendar
##### READ_RANGE_MASK_xxx - Bits that control what properties about the calendar entries will be returned for CalReadRange.
---
```
#include <calapi.h>
```

**Symbolic Values :**

	READ_RANGE_MASK_DTSTART	  -  

	READ_RANGE_MASK_DTEND	  -  

	READ_RANGE_MASK_DTSTAMP	  -  

	READ_RANGE_MASK_SUMMARY	  -  

	READ_RANGE_MASK_CLASS	  -  

	READ_RANGE_MASK_PRIORITY	  -  

	READ_RANGE_MASK_RECURRENCE_ID	  -  

	READ_RANGE_MASK_SEQUENCE	  -  

	READ_RANGE_MASK_LOCATION	  -  

	READ_RANGE_MASK_TRANSP	  -  

	READ_RANGE_MASK_CATEGORY	  -  

	READ_RANGE_MASK_APPTTYPE	  -  

	READ_RANGE_MASK_NOTICETYPE	  -  

	READ_RANGE_MASK_STATUS	  -  

	READ_RANGE_MASK_ONLINE_URL	  -  Includes online meeting URL as well as any online meeting password or conf ID

	READ_RANGE_MASK_NOTESORGANIZER	  -  For performance reasons, the organizer may not be stored in ORGANIZER but rather in X-LOTUS-ORGANIZER to avoid lookups necessary to get the internet address.

	READ_RANGE_MASK_NOTESROOM	  -  For performance reasons, the organizer may not be stored in PARTICIPANT but rather in X-LOTUS-ROOM to avoid lookups necessary to get the internet address.

	READ_RANGE_MASK_ALARM	  -  Output alarm information for this entry


**Description :**




**See Also :**
---
