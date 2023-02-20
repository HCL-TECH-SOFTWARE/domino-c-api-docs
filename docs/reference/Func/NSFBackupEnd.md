##### Function : Backup
##### NSFBackupEnd - Deallocate the backup context.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFBackupEnd(

	DBHANDLE  hDB,
	DHANDLE  BackupContext,
	DWORD  Options);
```
**Description :**

This function will deallocate the backup context that was obtained from 
NSFBackupStart once all recorded updates on the file should have been 
processed.

**Parameters :**
Input :
hDB  -  The handle to the database that whose backup is to be terminated.

BackupContext  -  Handle to the backup context that was obtained from NSFBackupStart.

Options  -  Zero to deallocate the backup context once all recorded updates have been processed.  See BACKUPEND_xxx for more options.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_NOT_LOCAL - Database is remote.

ERR_NOT_DOING_BACKUP - No backup is underway.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.



**Sample Usage :**
```
   /* Done with the backup */
   NSFBackupEnd(hDB, BackupContext, 0);

```
**See Also :**
[BACKUPEND_xxx](/reference/Symb/BACKUPEND_xxx)
[NSFBackupStart](/reference/Func/NSFBackupStart)
[NSFBackupStop](/reference/Func/NSFBackupStop)
---
