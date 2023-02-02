##### Function : Alarms
##### Alarm_RefreshAlarms - Refresh the Alarms list.
---
##### #include <alarm.h>
STATUS LNPUBLIC **Alarm_RefreshAlarms(**

	char far *pszClientName);
**Description :**
Alarm daemon should re-check the mailfile and refresh the list of alarms 
because new alarms might have been added or deleted.
**Parameters :**
Input :
pszClientName  -  The client whose alarms should be refreshed.

Output :
(routine)  -  NOERROR - Successfully refreshed alarms.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**See Also :**
[Alarm_ProcessAlarm](D:/md_files/Alarm_ProcessAlarm.md)
---
