##### Function : Backup
##### NSFBackupGetNextChangeInfo - Get next portion of the backup change information.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFBackupGetNextChangeInfo(

	DBHANDLE  hDB,
	DHANDLE  hBackupContext,
	DWORD  Flags,
	char *Buffer,
	DWORD  BufferSize,
	DWORD *FilledSize);
```
**Description :**

This function returns the next portion of the change information for the copied 
database file.  The order of the returned data must be maintained when it is 
passed in for application to the copied file.

The change information is returned as a stream of bytes.  When the change 
information is applied to the copied database file, it must be passed to 
NSFBackupApplyNextChangeInfo in the same order as it is returned.

This function will not return any change information unless NSFBackupStop has 
been called.

**Parameters :**
Input :
hDB  -  The handle to the database on which the backup is being performed.

hBackupContext  -  Handle to the backup context that was obtained from NSFBackupStart.

Flags  -  Reserved, must be zero.

Buffer  -  Pointer to a buffer to receive the change image information.

BufferSize  -  Size of Buffer.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_NOT_LOCAL - Database is remote.

ERR_NOT_DOING_BACKUP - No backup is underway.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


FilledSize  -  Pointer to a DWORD to get the amount of change information data put in Buffer.


**Sample Usage :**
```
   if (err = NSFBackupGetNextChangeInfo(hDB,
                                        BackupContext,
                                        0,
                                        Buffer,
                                        BUFFER_SIZE,
                                        &FilledSize))
   {
      print_api_error (err);
      NSFBackupEndApplyChangeInfo(ApplyInfoContext, APPLYEND_ABORT);
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
[NSFBackupApplyNextChangeInfo](/reference/Func/NSFBackupApplyNextChangeInfo)
[NSFBackupGetChangeInfoSize](/reference/Func/NSFBackupGetChangeInfoSize)
[NSFBackupStart](/reference/Func/NSFBackupStart)
[NSFBackupStop](/reference/Func/NSFBackupStop)
---
