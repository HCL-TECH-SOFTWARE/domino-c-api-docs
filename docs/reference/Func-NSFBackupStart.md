##### Function : Backup
##### NSFBackupStart - Initiate backup of a database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFBackupStart(**

	DBHANDLE  hDB,
	DWORD  Flags,
	DHANDLE *BackupContext,
	DWORD *FileSizeLow,
	DWORD *FileSizeHigh);
**Description :**
This function will initiate the backup of a database and return a backup 
context to the caller.  The backup facility is only supported for local 
databases.
**Parameters :**
Input :
hDB  -  The handle to the database that you want to back up.

Flags  -  Reserved, must be zero.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_NOT_LOCAL - Database is remote.

ERR_CANT_BACKUP_DURING_COMPACT - In place compacting of database is in progress, backup is not possible.

ERR_BACKUP_ALREADY_IN_PROGRESS - A backup is already underway, another cannot be started.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


BackupContext  -  Pointer to a handle that will be set to the backup context to be used for subsequent calls.

FileSizeLow  -  Pointer to a DWORD that will be set to the low-order 32 bits of file size as of the start of the backup.

FileSizeHigh  -  Pointer to a DWORD that will be set to the high-order 32 bits of file size as of the start of the backup.

**Sample Usage :**
```
   /* Start recording changes to the file at the NSF level */
   if (err = NSFBackupStart(hDB,
                            0L,
                            &BackupContext,
                            &FileSizeLow,
                            &FileSizeHigh))
   {
      print_api_error (err);
      NSFDbClose(hDB);
      NotesTerm();
      exit (EXIT_FAILURE);
   }

```
**See Also :**
[NSFBackupEnd](D:/md_files/NSFBackupEnd.md)
[NSFBackupGetChangeInfoSize](D:/md_files/NSFBackupGetChangeInfoSize.md)
[NSFBackupGetNextChangeInfo](D:/md_files/NSFBackupGetNextChangeInfo.md)
[NSFBackupSetHighWaterMark](D:/md_files/NSFBackupSetHighWaterMark.md)
[NSFBackupStop](D:/md_files/NSFBackupStop.md)
---
