##### Function : Backup
##### NSFEndArchivingLogs - Terminate the archiving of transactional logs.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFEndArchivingLogs(**
void);
**Description :**
Terminate the archiving of transactional logs and allow other processes to 
archive the log files.
**Parameters :**

Output :
(routine)  -  Return status from this call indicates either success or what the error is. The return codes include:

NOERROR - Success.  No other process is currently archiving logs.

ERR_SERVER_NOT_TRANSLOGGED - Transactional logging is not in effect.

ERR_TRANSLOG_NOT_ARCHIVED - Wrong logging style (circular).

ERR_TRANSLOG_ARCHIVE_IN_PROGRESS - Another process is currently archiving logs.


**Sample Usage :**
```
   if (err = NSFEndArchivingLogs ())
   {
      sprintf(EventString,
              "*** ERROR archiving logs *** (%s) : ",
              print_api_error(err));
      EventLog(LogFD, EventString);
   }

```
**See Also :**
[](D:/md_files/.md)
---
