##### Function : Backup
##### NSFBackupStartApplyChangeInfo - Initiate application of the backup change information.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFBackupStartApplyChangeInfo(**

	DHANDLE *ApplyInfoContext,
	char *CopyFilePath,
	DWORD  Flags,
	DWORD  InfoSizeLow,
	DWORD  InfoSizeHigh);
**Description :**
This function will initiate the application of the backup change information to 
a copy of a database file taken during a backup operation.  Once successfully 
started NSFBackupEndApplyChangeInfo must be called to free allocated resources.
**Parameters :**
Input :

CopyFilePath  -  Path to the file copied during the backup.

Flags  -  Reserved, must be zero.

InfoSizeLow  -  The low-order 32 bits of change information size.

InfoSizeHigh  -  The high-order 32 bits of change information size.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


ApplyInfoContext  -  Handle to the apply info context.

**Sample Usage :**
```
   /* Initiate getting the change info */
   if (err = NSFBackupStartApplyChangeInfo(&ApplyInfoContext,
                                           backup_file,
                                           0,
                                           InfoSizeLow,
                                           InfoSizeHigh))
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
[NSFBackupGetChangeInfoSize](D:/md_files/NSFBackupGetChangeInfoSize.md)
---
