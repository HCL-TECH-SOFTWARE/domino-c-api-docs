##### Function : Domino Upgrade Services
##### DUSRegistrationNotify - Notify registration is about to begin or is complete.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSRegistrationNotify(**

	DHANDLE  hContext,
	char *UserName,
	NOTEHANDLE  hUserNote,
	BOOL  bAfterEvent);
**Description :**
Notifies the DUS that Domino user registration for the user represented by 
UserName is about to start or just finished.  This allows the DUS to take pre 
or post registration action to supplement registration-releated activity.
**Parameters :**
Input :
hContext  -  handle to this DUS' specific context information.

UserName  -  LMBCS string identifying the user begin registered.

hUserNote  -  handle to the user note.

bAfterEvent  -  FALSE if the notification is just prior to user registration.
TRUE if the notification is just after user registration.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**See Also :**
[](D:/md_files/.md)
---
