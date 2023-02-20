##### Function : Alarms
##### Alarm_DeregisterInterest - Deregister interest in alarms.
---
```
#include <alarm.h>
STATUS LNPUBLIC Alarm_DeregisterInterest(

	char far *pszClientName,
	WORD  Flags);
```
**Description :**

Called by the client when it is terminating.  The alarms process will remove 
this client from its list.  If the list is empty the Alarms daemon will also 
terminate.

**Parameters :**
Input :
pszClientName  -  The client name.

Flags  -  Unused, pass in 0.

Output :
(routine)  -  NOERROR - Successfully deregistered interest in alarms.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.




**See Also :**
[Alarm_RegisterInterest](/reference/Func/Alarm_RegisterInterest)
---
