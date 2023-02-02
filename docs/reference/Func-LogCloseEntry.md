##### Function : Log
##### LogCloseEntry - Deallocates an unwanted log entry.
---
##### #include <log.h>
void LNPUBLIC **LogCloseEntry(**

	WORD  LogEntry);
**Description :**
Given the number associated with a new or partially completed log entry, this 
function discards all items associated with the entry and deallocates the log 
entry without writing the entry to the log file.

Use LogCompleteEntry to write a completed log entry to the log file.
**Parameters :**
Input :
LogEntry  -  A WORD containing the number of the log entry you wish to discard.  

Output :
(routine)  -  None.


**Sample Usage :**
```
/* Never mind this log entry, throw it away!!! */

LogCloseEntry(log_entry);
```
**See Also :**
[LogCreateEntry](D:/md_files/LogCreateEntry.md)
[LogCompleteEntry](D:/md_files/LogCompleteEntry.md)
---
