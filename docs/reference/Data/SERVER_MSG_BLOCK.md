##### Data Type : Message Queues
##### SERVER_MSG_BLOCK - Collector message queue server message structure.
---
```
#include <stats.h>
```
**Description :**

This is the structure of a message that can be put into the collection message 
queue (COLLECT_QUEUE_NAME in stdnames.h).

	DWORD Task The Collector Daemon task that is requested.  See xxx_TASK.
	DWORD Interval The interval to return information in minutes.
	char StatName[MAXSPRINTF] Statistics name in the form 
FacilityName.StatName.  For example, "Server.Users".
	char StatServerName[MAXPATH] Name of the server that you want 
information about.
	char MonitorServerName[MAXPATH] If Collection server is remote, provide 
poxy server name, otherwise set to NULL.
	DWORD MonitorFlags Reserved.  Must be set to 0.
	DHANDLE hTaskList Reserved.  Must be set to NULLHANDLE.
	DWORD  TaskListLen Reserved.  Must be set to 0.
	DHANDLE hStatList Reserved.  Must be set to NULLHANDLE.
	DWORD StatList Len Reserved.  Must be set to 0.
	char QueueName[20] Used by remote collector to pass information to 
proxy collector.  Otherwise set to NULL.
	
	

**See Also :**
[MQGet](/reference/Func/MQGet)
[MQPut](/reference/Func/MQPut)
[STAT_RETURN_BLOCK](/reference/Data/STAT_RETURN_BLOCK)
[xxx_TASK](/reference/Symb/xxx_TASK)
---
