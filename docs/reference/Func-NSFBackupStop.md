##### Function : Backup
##### NSFBackupStop - Halt the backup of a database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFBackupStop(**

	DBHANDLE  hDB,
	DHANDLE  BackupContext);
**Description :**
This function is called when the raw backup copy of the database has completed 
at the operating system level, to stop recording the before-image change 
information for the database.
**Parameters :**
Input :
hDB  -  The handle to the database on which the backup is being performed.

BackupContext  -  Handle to the backup context that was obtained from NSFBackupStart.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_NOT_LOCAL - Database is remote.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.


**Sample Usage :**
```
   /* Stop recording changes */
   NSFBackupStop(hDB, BackupContext);


```
**See Also :**
[NSFBackupStart](D:/md_files/NSFBackupStart.md)
---
