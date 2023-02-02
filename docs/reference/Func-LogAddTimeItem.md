##### Function : Log
##### LogAddTimeItem - Add a Time/Date to a log entry.
---
##### #include <log.h>
STATUS LNPUBLIC **LogAddTimeItem(**

	WORD  LogEntry,
	WORD  Flags,
	char far *ItemName,
	TIMEDATE far *Time);
**Description :**
This function takes a log entry number,  an entry lock flag, the name of the 
item, and the TIMEDATE value you wish to add to the log entry.  It deletes any 
existing item with the same name before adding the new value.
**Parameters :**
Input :
LogEntry  -  A WORD containing the number of the log entry to use.

Flags  -  A WORD flag that determines how often the log entry is flushed to disk.  If LOG_LEAVE_LOCKED is specified, then the log entry is not written to disk until it is completed, to preseve the consistency of the fields in the entry.  If 0 is specified (the default), then the partially completed log entry is flushed to disk every so often so that it can be seen in the Log database.

ItemName  -  A null-terminated item name of the item to be added to the log entry.

Time  -  A pointer to a TIMEDATE structure containing the Time/Date you wish to append to the log entry.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added Time/Date to log entry.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display the error for the user.


**Sample Usage :**
```
/* Log Time of day in an AddInEvent note */

OSCurrentTIMEDATE(&log_td);
if (error_status = LogAddTimeItem(log_entry, LOG_LEAVE_LOCKED,
                                     "SpecialTime", &log_td))
   goto Exit;
```
**See Also :**
[LogCreateEntry](D:/md_files/LogCreateEntry.md)
[LogAddNumberItem](D:/md_files/LogAddNumberItem.md)
[LogAddText](D:/md_files/LogAddText.md)
[LogAddTextlistItem](D:/md_files/LogAddTextlistItem.md)
[LogCompleteEntry](D:/md_files/LogCompleteEntry.md)
---
