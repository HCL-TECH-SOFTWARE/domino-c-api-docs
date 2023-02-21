##### Function : Extension Manager
##### SMTPConnectEMCallback - Extension Manager callback for EM_SMTPCONNECT
---
```
#include <extmgr.h>
STATUS LNPUBLIC SMTPConnectEMCallback(

	DWORD  SessionID,
	char *RemoteIP,
	char *RemoteHost,
	BOOL &  PossibleRelay,
	char *Greeting,
	DWORD  MaxGreetingLength);
```
**Description :**

EM_SMTPCONNECT is called when an inbound SMTP connection has been detected.
	
The Extension Manager EM_BEFORE notification type for the EM_SMTPCONNECT event 
occurs when an inbound SMTP connection has been detected and prior to the 
execution of the internal Domino SMTP restriction controls.  The callback 
routine can implement its own anti-relay checks and/or bypass Domino related 
checks through the use of PossibleRelay BOOL and return status of value 
NOERROR.  Return STATUS other than ERR_EM_CONTINUE or NOERROR sets AccessDenied 
flag which causes subsequent commands to be rejected.  

The Extension Manager EM_AFTER notification type for the EM_SMTPCONNECT event 
occurs after the SMTP listener task has accepted the connection but prior to 
sending the SMTP greeting to the connecting host.

**Parameters :**
Input :
SessionID  -  Unique session identifier for the current process.

RemoteIP  -  NULL terminated string containing IP address of connecting host.

RemoteHost  -  NULL terminated string containing host name of connecting host if reverse DNS lookup was successful.  If lookup was unsuccessful, the string length will be zero. 

PossibleRelay  -  Indicator whether connecting host should be treated as possible relay or not.

MaxGreetingLength  -  Size of buffer allocated to modify Greeting.

Output :
(routine)  -  Return status from the call 
EM_BEFORE event: NOERROR indicates to skip configured relay and RBL checks; Value other than  ERR_EM_CONTINUE indicates further commands should be rejected from host.
EM_AFTER event: Value other than ERR_EM_CONTINUE is ignored.


Greeting  -  EM_BEFORE event: NULL; EM_AFTER event: Greeting that will be returned to the connecting host.  Callback routine can modify the string.


**See Also :**
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
---
