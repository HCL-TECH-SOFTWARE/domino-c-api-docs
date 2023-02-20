##### Function : Alarms
##### Alarm_ProcessAlarm - Indicate alarm has been processed.
---
```
#include <alarm.h>
STATUS LNPUBLIC Alarm_ProcessAlarm(

	char far *pszClientName,
	WORD  wSnoozeMinutes,
	UNID  EventUNID,
	WORD  Flags);
```
**Description :**

Sent by the client after it has processed an alarm by displaying it to the user 
and getting the OK or SNOOZE from the user.

**Parameters :**
Input :
pszClientName  -  Handle of the caller's name who was asked to display the alarm.

wSnoozeMinutes  -  How much to snooze the alarm by (0 if not to be snoozed)

EventUNID  -  UNID of the event which is to be processed.

Flags  -  Not currently used, pass in 0.

Output :
(routine)  -  NOERROR - Successfully processed the alarm.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[Alarm_RefreshAlarms](/reference/Func/Alarm_RefreshAlarms)
---
