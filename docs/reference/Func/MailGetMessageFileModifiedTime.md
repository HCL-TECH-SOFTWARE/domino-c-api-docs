##### Function : Mail Gateway
##### MailGetMessageFileModifiedTime - Returns the timestamp of last modification time of a message file.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailGetMessageFileModifiedTime(

	DBHANDLE  hFile,
	TIMEDATE far *retModifiedTime);
```
**Description :**

This function returns the timestamp of the last modification time of the 
message file.  It can be used by a gateway to determine if new messages have 
been added to the file since the last time it checked.

**Parameters :**
Input :
hFile  -  Open message file handle.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


retModifiedTime  -  Time/date of last modification of message file (e.g. time/date last message was added/deleted.


**See Also :**
[NSFDbModifiedTime](/domino-c-api-docs/reference/Func/NSFDbModifiedTime)
[MailGetMessageItemTimeDate](/domino-c-api-docs/reference/Func/MailGetMessageItemTimeDate)
---
