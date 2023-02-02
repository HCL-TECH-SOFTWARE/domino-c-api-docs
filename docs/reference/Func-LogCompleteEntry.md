##### Function : Log
##### LogCompleteEntry - Allow writing the log entry to disk.
---
##### #include <log.h>
STATUS LNPUBLIC **LogCompleteEntry(**

	WORD  LogEntry);
**Description :**
Given the number of a log entry, this function adds an item called FinishTime 
to the entry and marks the entry "complete", "modified", and "not locked", 
allowing the entry to be written to disk and deallocated.  Log entries are 
written to disk at set intervals or when a client or server component attempts 
to read from the log (to ensure that the request obtains the most up-to-date 
information).  In addition, if any log messages have not been written to disk 
when the API program terminates, these messages are written at that time.
**Parameters :**
Input :
LogEntry  -  A WORD containing the number of the log entry you would like to write to the Log database.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully completed the log entry.

ERR_LOG_NULLHANDLE - Log Entry not allocated.  The Log Package is no longer available.

ERR_LOGENTRY_INVALID - LogEntry out of range.

ERR_LOG_RESERVED_ENTRY - LogEntry reserved.  Meaning that the log entry number supplied is less than or equal to MAX_RESERVED_LOG_ENTRY.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display the error for the user.


**Sample Usage :**
```
/* Automatically fill FinishTime item/field  and recycle the log */
/* entry(unlocks the object)                                     */

if (error_status = LogCompleteEntry(log_entry))
   goto Exit;
else
   cleanup_state -= COMPLETE_LOG_ENTRY;
```
**See Also :**
[LogCloseEntry](D:/md_files/LogCloseEntry.md)
[LogCreateEntry](D:/md_files/LogCreateEntry.md)
---
