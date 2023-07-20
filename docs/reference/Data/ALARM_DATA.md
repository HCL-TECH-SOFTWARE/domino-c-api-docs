##### Data Type : Alarms
##### ALARM_DATA - Alarm structure.
---
```
#include <alarm.h>
```

**Definition :**
```
typedef struct {
   TIMEDATE tmEventTime;    /* Time for the event  */
   TIMEDATE tmAlarmTime;    /* Time for the alarm */
   DHANDLE   hSubject;       /* Handle to alarm subject */
   WORD     Flags;          /* see ALARM_DATA_FLAG_xxx */
   UNID     EventUNID;      /* UNID for the event note */
   DHANDLE   hAlarmTuneName; /* Tune to play */
   DHANDLE   hSendMailAddr;  /* Address to send message to */
} ALARM_DATA;
```

**Description :**

Message structure sent TO THE CLIENT, one per alarm.  There is an array of these structures pointed to by ALARM_MSG.


**See Also :**
[ALARM_DATA_FLAG_xxx](/domino-c-api-docs/reference/Symb/ALARM_DATA_FLAG_xxx)
---
