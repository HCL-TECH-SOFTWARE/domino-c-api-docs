##### Function : Backup
##### NSFDbGetLogInfo - Check if database is logged.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbGetLogInfo(**

	DBHANDLE  hDb,
	DWORD  Flags,
	BOOL *LOGGED,
	UNID *LogID,
	UNID *DbIID,
	DWORD *LogExtent);
**Description :**
Check if database is logged.
**Parameters :**
Input :
hDb  -  Handle to database.

Flags  -  Reserved, must be zero.

Output :
(routine)  -  Return status from this call indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_NOT_LOCAL - Database is remote.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


LOGGED  -  Pointer to BOOL.  TRUE if database is currently logged, otherwise FALSE.

LogID  -  Pointer to the UNID of a database if it is logged.

DbIID  -  Pointer to the databases instance id (DBIID) of a database if it is logged.

LogExtent  -  Pointer to a DWORD set to the first log extent that will be needed to restore the next backup taken.

**Sample Usage :**
```
   /* Check to see if DB is being logged. */
   if (err = NSFDbGetLogInfo(hDB, 0L, &Logged, &LogID, &DbIID, &LogExtent))
   {
      print_api_error (err);
      NSFBackupEnd(hDB, BackupContext, BACKUPEND_ABORT);
      NSFDbClose(hDB);
      NotesTerm();
      exit (EXIT_FAILURE);
   }
   if(!Logged)
   {
      printf("\n  Database '%s' is not currently logged ...\n", path_name);
      printf("\n  Resulting backup file '%s' WILL NOT BE RECOVERABLE ...\n", 
backup_file);
   }

```
**See Also :**
[](D:/md_files/.md)
---
