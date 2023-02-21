##### Function : Backup
##### NSFBackupGetChangeInfoSize - Get size of the backup change information.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFBackupGetChangeInfoSize(

	DBHANDLE  hDB,
	DHANDLE  hBackupContext,
	DWORD  Flags,
	DWORD *InfoSizeLow,
	DWORD *InfoSizeHigh);
```
**Description :**

This function will return the total size in bytes of the change information for 
the copied database file.

This function will not return any change information unless NSFBackupStop has 
been called.

**Parameters :**
Input :
hDB  -  The handle to the database on which the backup is being performed.

hBackupContext  -  Handle to the backup context that was obtained from NSFBackupStart.

Flags  -  Reserved, must be zero.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_NOT_LOCAL - Database is remote.

ERR_NOT_DOING_BACKUP - No backup is underway.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


InfoSizeLow  -  Pointer to DWORD to get the low 32 bits of change information size.

InfoSizeHigh  -  Pointer to DWORD to get the high 32 bits of change information size.


**Sample Usage :**
```
   /* Get the change info size */
   if (err = NSFBackupGetChangeInfoSize(hDB,
                                        BackupContext,
                                        0,
                                        &InfoSizeLow,
                                        &InfoSizeHigh))
   {
      print_api_error (err);
      OSUnlockObject(hBuffer);
      OSMemFree(hBuffer);
      OSFileDelete(backup_file);
      OSFileClose(srcfd);
      NSFBackupEnd(hDB, BackupContext, BACKUPEND_ABORT);
      NSFDbClose(hDB);
      NotesTerm();
      exit (EXIT_FAILURE);
   }

```
**See Also :**
[NSFBackupStart](/domino-c-api-docs/reference/Func/NSFBackupStart)
[NSFBackupStartApplyChangeInfo](/domino-c-api-docs/reference/Func/NSFBackupStartApplyChangeInfo)
[NSFBackupStop](/domino-c-api-docs/reference/Func/NSFBackupStop)
---
