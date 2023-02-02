##### Function : Alarms
##### Alarm_ChangeLocation - Reread location for the new user.
---
##### #include <alarm.h>
STATUS LNPUBLIC **Alarm_ChangeLocation(**

	char far *pszClientName,
	WORD  Flags);
**Description :**
Tell the alarm manager to reread location information for this new user.
**Parameters :**
Input :
pszClientName  -  The client name.

Flags  -  Pass in 0.

Output :
(routine)  -  NOERROR - Successfully told alarm manager to change location.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**See Also :**
[Alarm_RefreshAlarms](D:/md_files/Alarm_RefreshAlarms.md)
---
