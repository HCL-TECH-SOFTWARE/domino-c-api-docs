##### Data Type : User Registration
##### REG_ROAMING_INFO - Structure that defines roaming registration information.
---
```
#include <reg.h>
```

**Definition :**

typedef struct
	{
	DWORD Size;   /* size of this structure - must initialize with sizeof 
(REG_ROAMING_INFO) */
	char *ServerName;  /* server destination for three roaming files */
	char *SubDirectory;  /* path (relative) to data dir on which roaming 
files will be created */
	WORD CleanupSetting;  /* REG_ROAMING_CLEANUP_NEVER is don't cleanup
	      REG_ROAMING_CLEANUP_EVERY_NDAYS is cleanup every ndays
	      REG_ROAMING_CLEANUP_AT_SHUTDOWN is cleanup at shutdown
	      REG_ROAMING_CLEANUP_PROMPT is prompt for cleanup*/
	WORD CleanupPeriod;  /* for REG_ROAMING_CLEANUP_EVERY_NDAYS - days, 
values 1 through 365 allowed */
	DHANDLE hReplicaServers; /* text list of replica servers */
       	WORD OnDuplicate;  /* one of REG_FILE_DUP_XXX */

	DWORD Reserved[4];
	void *pReserved[4];
	} REG_ROAMING_INFO;



**Description :**

<br>
This structure defines roaming registration information for the REGNewPerson function.  The entire structure must be initialized to zero.<br>

<ul>The fields in the structure are (all fields that are not used must be NULL/O):<br>
<br>
Size		Size of this structure - must be initialized with sizeof (REG_ROAMING_INFO).<br>
ServerName	Destination server name for the roaming files.<br>
SubDirectory	Path (relative) to data dir on which roaming files will be created.<br>
CleanupSetting	The cleanup setting used by the roaming client (see REG_ROAMING_CLEANUP_XXX).<br>
CleanupPeriod	Number of days between cleanup (1 - 365) for REG_ROAMING_CLEANUP_EVERY_NDAYS.<br>
hReplicaServers	(Optional.) Handle to a text list of server names where replica stubs of the roaming files should be created.  The list should be constructed with ListAllocate and ListAddEntry.  </ul>
<tt><font size="2">&nbsp; </font></tt><tt>&nbsp; OnDuplicate &nbsp; &nbsp; &nbsp;one of REG_FILE_DUP_XXX.</tt><br>
    Reserved		Reserved - must be 0.
<ul>pReserved		Reserved - must be NULL.</ul>



**See Also :**
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[REGNewPerson](/domino-c-api-docs/reference/Func/REGNewPerson)
[REG_FILE_DUP_xxx](/domino-c-api-docs/reference/Symb/REG_FILE_DUP_xxx)
[REG_ROAMING_CLEANUP_xxx](/domino-c-api-docs/reference/Symb/REG_ROAMING_CLEANUP_xxx)
---
