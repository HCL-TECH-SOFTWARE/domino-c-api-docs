##### Symbolic Value : Calendaring and Scheduling
##### SCHEDAPPLID_xxx - SCHED_LIST - wApplicationID
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	SCHEDAPPLID_ORGANIZER2X	  -  Lotus Organizer 2.x.

	SCHEDAPPLID_ORGANIZER4X	  -  Lotus Organizer 4.x

	SCHEDAPPLID_OV	  -  Improv.


**Description :**

These are application ID's for the SCHED_LIST wApplicationID field.  This is used to interpret the application specific UserAttr field in the SCHED_ENTRIES records.  Domino ignores the UserAttr field, howerver application specific information can be returned by application specific gateways.  If you need an ID, please register it with Lotus.


**See Also :**
[SCHED_LIST](/domino-c-api-docs/reference/Data/SCHED_LIST)
[SCHED_ENTRY](/domino-c-api-docs/reference/Data/SCHED_ENTRY)
---
