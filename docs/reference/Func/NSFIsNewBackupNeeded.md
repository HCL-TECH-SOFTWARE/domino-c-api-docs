##### Function : Backup
##### NSFIsNewBackupNeeded - Check if the specified file needs a new backup.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFIsNewBackupNeeded(

	const char far *dbName,
	DWORD  comfortSpan,
	DWORD far *backupNeeded);
```
**Description :**

Determine the state of the database or database backup file with respect to the 
current log state.  This function either returns a boolean (0 or 1 value) for 
backupNeeded, if a comfortSpan is supplied (specified in K bytes), or returns 
the actual span of log needed for recovery, if a comfortSpan of 0 is supplied.  
The comfortSpan is the amount of log to be remaining before the backup would be 
made useless by a logging wrap in a 'CIRCULAR' or 'LINEAR' type logged system 
(see Transactional Logging settings in the Administering the Domino System 
documentation).

The purpose of this function is to allow simple scheduled backups when needed.  
An example use: by calling this function with a comfortSpan of 327680 at 10PM 
and 65536 through-out the day (hourly) for a system with 2GB of log, you could 
encourage nightly backups but initiate them during the day if comfortSpan deems 
it necessary.

**Parameters :**
Input :
dbName  -  Database or database backup file name.

comfortSpan  -  Amount of log (specified in K bytes) to be remaining before the backup would be made useless by a logging wrap in a 'CIRCULAR' or 'LINEAR' type logged system (see Transactional Logging settings in the Domino Administration Guide).  A comfortSpan of '0' will return the actual log span, the amount of log needed to process to recover the database.

For 'CIRCULAR' or 'LINEAR' type logging the minimum comfortSpan specified, other than 0, should be 65536 (64MB) as you need to leave at least one extent available for logging.

For 'ARCHIVE' type logging, only  a comfortSpan of 0 is supported.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_ONLY_V5_DATABASES - The database file is not in R5 format or is not logged.

ERR_RM_RECOVER_NONBACKUP - The database has not been backed up on this server/instance of the log.

ERR_RM_GENERAL_FAILURE - The server is not logged.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


backupNeeded  -  Returns either a boolean (0 or 1 value), if a comfortSpan is supplied (specified in K bytes), or the actual span of log needed for recovery if a comfortSpan of 0 is supplied.


**Sample Usage :**
```
   err = NSFIsNewBackupNeeded(BUPath, ComfortSpan, &BackupNeeded);

   if (!err)
   {
      sprintf(EventString, "Backup file %s checked - ", BUPath);

      if (ComfortSpan)
      {
         if (BackupNeeded)
    strcat(EventString, "New Backup is needed");
         else
    strcat(EventString, "New Backup is NOT needed");
      }
      else
      {
            sprintf(EventString2, "Span of log is %d", BackupNeeded);
            strcat(EventString, EventString2);
      }

      EventLog(LogFD, EventString);
      printf("\n  %s\n", EventString);
   }
   else
   {
      sprintf(EventString,
              "*** ERROR checking backup file %s *** (%s)",
              BUPath,
              print_api_error(err));
      EventLog(LogFD, EventString);
   }
```
**See Also :**
---
