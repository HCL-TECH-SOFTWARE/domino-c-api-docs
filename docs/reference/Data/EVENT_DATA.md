##### Data Type : Events
##### EVENT_DATA - Data structure used by the event handling routines.
---
```
#include <event.h>
```

**Definition :**

typedef struct  {
	 DWORD Links[3];   /* Reserved - used to link this struct onto queues */
	 char OriginatingServerName[MAXUSERNAME]; /* Server name (only if event 
relayed to another server) */
	 WORD Version;   /* EVENT_VERSION */
	 WORD ErrorCode;   /* Error code (any values) associated with this 
event */
	 WORD AdditionalErrorCode; /* Additional Error code (any values) 
associated with this event */
	 WORD AddinNameLength;  /* Length of AddinName at end of structure */
	 WORD Type;    /* EVT_xxx */
	 WORD Severity;   /* SEV_xxx */
	 TIMEDATE EventTime;  /* Time/date event was generated */
	 WORD FormatSpecifier;  /* FMT_xxx (format of event data which follows) 
*/
	 WORD EventDataLength;  /* Length of event data which follows */
	 BYTE EventSpecificData;  /* (First byte of) Event Data which 
follows... */
	      /* (AddinName string follows...) */
	} EVENT_DATA;

**Description :**

This data structure contains all the data necessary to define an event.  A handle to an EVENT_DATA structure is returned as output by the function EventQueueGet.


**See Also :**
[EventDeregisterEventRequest](/domino-c-api-docs/reference/Func/EventDeregisterEventRequest)
[EventGetDestName](/domino-c-api-docs/reference/Func/EventGetDestName)
[EventQueueAlloc](/domino-c-api-docs/reference/Func/EventQueueAlloc)
[EventQueueFree](/domino-c-api-docs/reference/Func/EventQueueFree)
[EventQueueGet](/domino-c-api-docs/reference/Func/EventQueueGet)
[EventQueuePut](/domino-c-api-docs/reference/Func/EventQueuePut)
[EventRegisterEventRequest](/domino-c-api-docs/reference/Func/EventRegisterEventRequest)
[EVT_xxx](/domino-c-api-docs/reference/Symb/EVT_xxx)
[SEV_xxx](/domino-c-api-docs/reference/Symb/SEV_xxx)
---
