##### Function : Calendaring and Scheduling
##### SchMsgQHandles_New - Prepare message queues.
---
##### #include <schgtw.h>
STATUS LNPUBLIC **SchMsgQHandles_New(**

	char FAR *szServerName,
	BOOL  fCreate,
	MQHANDLE FAR *rethInputQ,
	MQHANDLE FAR *rethOutputQ);
**Description :**
This prepares the message queues that we send/receive messages on.
**Parameters :**
Input :
szServerName  -  Points to the server name, if it is NULL then this is a native Domino request, else this is the name of the gateway.

fCreate  -  Set this to TRUE if the queues should be created if they don't already exist. Note: only the "gateway" should create the queues. Alls gateway clients should pass this parameter as FALSE.

Output :
(routine)  -  NOERROR - Successfully prepared the message queue.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethInputQ  -  Points to where we return the handle to the input queue

rethOutputQ  -  Points to where we return the handle to the output queue.

**See Also :**
[SchMsgQHandles_Free](D:/md_files/SchMsgQHandles_Free.md)
---
