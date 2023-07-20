##### Data Type : Message Queues
##### SERVER_MSG_BLOCK - Collector message queue server message structure.
---
```
#include <stats.h>
```

**Definition :**
```
typedef struct {
   DWORD  Task;                       /* Task to be processed by
                                         collector
                                         (i.e., Add server) */
   DWORD  Interval;                   /* Interval to return info in
                                         minutes */
   char   StatName[MAXSPRINTF];       /* REMOVE */
   char   StatServerName[MAXPATH];    /* Name of server that you
                                         want info about */
   char   MonitorServerName[MAXPATH]; /* If remote provide proxy
                                         server name otherwise
                                         NULL */
   DWORD  MonitorFlags;               /* Flags passed to monitor
                                         (Reports, Alarms, ...) */
   DHANDLE hTaskList;                  /* List of user defined tasks
                                         to monitor */
   DWORD  TaskListLen;                /* Size of stat list */
   DHANDLE hStatList;                  /* List of stats to return to
                                         monitor */
   DWORD  StatListLen;                /* Size of stat list */
   char   QueueName[20];              /* Used by remote collector
                                         to pass info to proxy
                                         collector */
} SERVER_MSG_BLOCK;
```

**Description :**

This is the structure of a message that can be put into the collection message queue (COLLECT_QUEUE_NAME in stdnames.h).<br>
<br>
	DWORD	Task	The Collector Daemon task that is requested.  See xxx_TASK.<br>
	DWORD	Interval	The interval to return information in minutes.<br>
	char	StatName[MAXSPRINTF]	Statistics name in the form FacilityName.StatName.  For example, &quot;Server.Users&quot;.<br>
	char	StatServerName[MAXPATH]	Name of the server that you want information about.<br>
	char	MonitorServerName[MAXPATH]	If Collection server is remote, provide poxy server name, otherwise set to NULL.<br>
	DWORD	MonitorFlags	Reserved.  Must be set to 0.<br>
	DHANDLE	hTaskList	Reserved.  Must be set to NULLHANDLE.<br>
	DWORD 	TaskListLen	Reserved.  Must be set to 0.<br>
	DHANDLE	hStatList	Reserved.  Must be set to NULLHANDLE.<br>
	DWORD	StatList Len	Reserved.  Must be set to 0.<br>
	char	QueueName[20]	Used by remote collector to pass information to proxy collector.  Otherwise set to NULL.<br>
	<br>
	


**See Also :**
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[STAT_RETURN_BLOCK](/domino-c-api-docs/reference/Data/STAT_RETURN_BLOCK)
[xxx_TASK](/domino-c-api-docs/reference/Symb/xxx_TASK)
---
