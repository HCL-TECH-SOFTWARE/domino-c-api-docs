##### Function : Alarms
##### Alarm_RegisterInterest - Register interest in receiving alarms.
---
##### #include <alarm.h>
STATUS LNPUBLIC **Alarm_RegisterInterest(**

	char far *pszClientName,
	WORD  Flags);
**Description :**
Register this client as having an interest in receiving alarms. Alarms daemon 
will be started if none running.
**Parameters :**
Input :
pszClientName  -  Standard name of the client which will be used by the alarms daemon to determine if this is a preferred client for displaying alarms.

Flags  -  Not used, pass in 0.

Output :
(routine)  -  NOERROR - Successfully registered interest in receiving alarms.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[Alarm_DeregisterInterest](D:/md_files/Alarm_DeregisterInterest.md)
---
