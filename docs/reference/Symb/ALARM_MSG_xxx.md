##### Symbolic Value : Alarms
##### ALARM_MSG_xxx - ALARM_MSG - Type
---
```
#include <alarm.h>
```

**Symbolic Values :**

	ALARM_MSG_PENDING_ALARMS	  -  Message sent when there are 'past alarms' - alarms prior to today which haven't been displayed to the user. Client will get a buffer with all the past alarms and a count of how many alarms there are. All the alarms have the structure defined in this file.

	ALARM_MSG_NEW_ALARM	  -  Sent by the alarms daemon when there is a new alarm which needs to be displayed.

	ALARM_MSG_IS_TERMINATING	  -  Sent by the alarms daemon to all clients before it terminates.


**Description :**

Messages sent by the alarms daemon in the MQ of the client.  Client should periodically check it's queue in order to receive these and do the appropriate tasks.


**See Also :**
[ALARM_MSG_xxx](/domino-c-api-docs/reference/Symb/ALARM_MSG_xxx)
---
