##### Function : Backup
##### NSFRecoverDatabases - Recover specified databases.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFRecoverDatabases(

	const char far *dbNames,
	LOGRESTORECALLBACKFUNCTION  restoreCB,
	DWORD  Flags,
	WORD far *errDbIndex,
	TIMEDATE far *recoveryTime);
```
**Description :**

This function will apply all updates to the backup of one or more logged 
databases.

**Parameters :**
Input :
dbNames  -  Pointer to a list of one or more database file names to be recovered.  For a list containing multiple database names, each dbName must be null terminated and there must be a second null termination after the last dbName, to terminate the entire list.

restoreCB  -  The Log Restore Callback function pointer.  This function is called during the recovery if archived log extents are needed.  NULL should be passed if you are not using ARCHIVE style logging.

Flags  -  Specification of recovery options, see DBRECOVER_xxx.

recoveryTime  -  Only required with the DBRECOVER_POINT_IN_TIME option where it specifies the point in time to recover to.  All committed transactions completed prior to that time are applied to the list of databases. 

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_RM_LATE_BACKUP - Backup is later than point in time specified for recovery. You must find an earlier backup. The backups are unaffected.

ERR_RM_RECOVER_NONBACKUP - Attempt to recover a db using a file that was not created with a Domino backup utility. The backups are unaffected.

ERR_RM_LOG_SPACE_CRITICAL  - Circular log was getting full, recover aborted. After this error the database cannot be recovered. the backups are corrupt.

ERR_RM_SCAN_IN_PROGRESS  - A scan is already in progress, try again later. Commonly indicates an active media recovery. The backups are unaffected.

ERR_RM_MQ_LOG_ERROR - Could not retrieve log extents needed for recovery. The backups are corrupt.

ERR_VALUE_FLAG - Invalid parameter. The backups are unaffected.

ERR_RM_FIXUP_DB - Backup was from a different system, the log was reformatted since the backup was taken or the backup is corrupt.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.


errDbIndex  -  The 1 based index of the database causing the error, if an error is returned.  A 0 is returned if the error cannot be associated with a database.  NULL if no database error index is desired.

recoveryTime  -  When supplied, it receives the time date of the last transaction applied to any of the databases recovered.  If NULL is provided, nothing is returned.


**Sample Usage :**
```
   if(Rflags)
   Rflags = DBRECOVER_ZAP_ID;

   if(RNoteInfo)
   {
      sprintf(EventString, "\nRecovering backup file %s with CallBack", BUPath);
      EventLog(LogFD, EventString);
      err = NSFRecoverDatabasesWithCallback(BUPath, MyCallback, Rflags, &index, 
NULL, NoteCallback, 0);
   }
   else
   {
 if (!Rflags)
    sprintf(EventString, "Recovering backup file %s", BUPath);
 else
    sprintf(EventString, "\nRecovering backup file %s", BUPath);
      EventLog(LogFD, EventString);
      err = NSFRecoverDatabases(BUPath, MyCallback, Rflags, &index, NULL);
   }

   if (!err)
   {
 while (BUPath[0] != '\0')
 {
         printf("\n Backup file %s recovered.", BUPath);
         sprintf(EventString, "Backup file %s recovery complete", BUPath);
         EventLog(LogFD, EventString);
         BUPath += strlen(BUPath) + 1;
 }
   }
   else
   {
 while (BUPath[0] != '\0')
 {
    errindex++;
    if(errindex ==index)
    {
             printf("\nError recovering backup file %s\n", BUPath);
             sprintf(EventString, " *** ERROR recovering backup file %s *** 
(%s)",
   BUPath,
   print_api_error(err));
   EventLog(LogFD, EventString);
          }
          BUPath += strlen(BUPath) + 1;
       }
   }
```
**See Also :**
[DBRECOVER_xxx](/reference/Symb/DBRECOVER_xxx)
[LOGRESTORECALLBACKFUNCTION](/reference/Data/LOGRESTORECALLBACKFUNCTION)
---
