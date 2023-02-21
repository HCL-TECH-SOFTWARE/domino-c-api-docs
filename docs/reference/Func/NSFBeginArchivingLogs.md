##### Function : Backup
##### NSFBeginArchivingLogs - Initiate the archiving of transactional logs.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFBeginArchivingLogs(
void);
```
**Description :**

Lock out other processes trying to archive the log files and initiate the 
archiving of transactional logs.

**Parameters :**

Output :
(routine)  -  Return status from this call indicates either success or what the error is. The return codes include:

NOERROR - No other process is currently archiving logs.

ERR_SERVER_NOT_TRANSLOGGED - Transactional logging is not in effect.

ERR_TRANSLOG_NOT_ARCHIVED - Wrong logging style (circular).

ERR_TRANSLOG_ARCHIVE_IN_PROGRESS - Another process is currently archiving logs.



**Sample Usage :**
```
   if (err = NSFBeginArchivingLogs ())
   {
      sprintf(EventString,
              "*** ERROR archiving logs *** (%s) : ",
              print_api_error(err));
      EventLog(LogFD, EventString);
      return 1;
   }

```
**See Also :**
[NSFDoneArchivingLog](/domino-c-api-docs/reference/Func/NSFDoneArchivingLog)
[NSFEndArchivingLogs](/domino-c-api-docs/reference/Func/NSFEndArchivingLogs)
[NSFGetFirstLogToArchive](/domino-c-api-docs/reference/Func/NSFGetFirstLogToArchive)
[NSFGetNextLogToArchive](/domino-c-api-docs/reference/Func/NSFGetNextLogToArchive)
---
