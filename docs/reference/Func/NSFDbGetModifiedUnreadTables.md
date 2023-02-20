##### Function : Database
##### NSFDbGetModifiedUnreadTables - Get modified unread tables.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetModifiedUnreadTables(

	DBHANDLE  hDB,
	char*UserName,
	WORD  UserNameLen,
	TIMEDATE  Since,
	TIMEDATE *Until,
	DHANDLE *hRead,
	DHANDLE *hUnread);
```
**Description :**

This function will get unread tables modified during a specific time period for 
local databases only.  A note will appear in only one IDTABLE when the routine 
is called.  If a note is marked read, and then marked unread, the note will 
only appear in the "unread" IDTABLE (hUnread).   If the database doesn't 
support unread replication, the tables will be returned empty.  The IDTables 
returned, which may be empty, must be destroyed after you are done with them 
(IDDestroyTable).

**Parameters :**
Input :
hDB  -  Handle to an open local database.

UserName  -  Pointer to a case sensitive canonical user name (ie. "CN=Moe Howard/O=orgname).

UserNameLen  -  User name length.

Since  -  A TIMEDATE structure that specifies the earliest time the unread table has been modified.  This is the internal database time - not necessarily the system time.  Databse time has different characteristics from the system time - such as the database time never can go backwards even if the system clock is set back.  The Since time is usually close to the system time (OSCurrentTIMEDATE), but not necessarily.  You should pass the value returned in the Until field the last time you called.  You really don't care what this time is, but you just want to make sure you saved the Until time from the previous call, and use that as the Since time.

Until  -  A pointer to a TIMEDATE structure containing a time/date value specifying the latest time the unread table was modified.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Modified unread tables successfully retrieved.

ERR_NOT_LOCAL - Function is not supported for remote databases.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.


Until  -  A pointer to the TIMEDATE for the last time in the log.  This will be returned to you when you call, and on the next call, you should use this as your Since time.

hRead  -  Pointer to a handle for an IDTABLE of noteIDs that were marked Read after Since time. It may be an empty table.

hUnread  -  Pointer to a handle for an IDTABLE of noteIDs that were marked Unread after the Since time.  It may be an empty table.


**See Also :**
[IDDestroyTable](/reference/Func/IDDestroyTable)
---
