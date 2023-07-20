##### Data Type : Alarms
##### ALARM_MSG - Alarms Daemon request message
---
```
#include <alarm.h>
```

**Definition :**
```
typedef struct {
   WORD   Type;         /* Type of request (ALARM_MSG_xxx) */
   WORD   Flags;        /* Options - not used now */
   WORD   wNumOfAlarms; /* Number of alarms */
   DHANDLE hAlarmsData;  /* Handle to an array of alarms structures */
} ALARM_MSG;
```

**Description :**

Structure defining the MQ request sent by the alarms daemon to the client who has registered for receiving alarms.


**See Also :**
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[Alarm_RegisterInterest](/domino-c-api-docs/reference/Func/Alarm_RegisterInterest)
[Alarm_RefreshAlarms](/domino-c-api-docs/reference/Func/Alarm_RefreshAlarms)
---
