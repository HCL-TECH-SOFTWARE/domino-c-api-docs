##### Data Type : Alarms
##### LPALARM_DATA - Alarm structure.
---
```
#include <alarm.h>
```

**Definition :**

typedef struct {
   TIMEDATE tmEventTime;    /* Time for the event  */
   TIMEDATE tmAlarmTime;    /* Time for the alarm */
   HANDLE   hSubject;       /* Handle to alarm subject */
   WORD     Flags;          /* see ALARM_DATA_FLAG_xxx */
   UNID     EventUNID;      /* UNID for the event note */
   DHANDLE   hAlarmTuneName; /* Tune to play */
   DHANDLE   hSendMailAddr;  /* Address to send message to */
} far *LPALARM_DATA;

**Description :**

Pointer to message structure sent TO THE CLIENT, one per alarm.  There is an array of these structures pointed to by ALARM_MSG.


**See Also :**
[ALARM_DATA](/domino-c-api-docs/reference/Data/ALARM_DATA)
---
