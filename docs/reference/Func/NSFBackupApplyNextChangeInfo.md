##### Function : Backup
##### NSFBackupApplyNextChangeInfo - Apply the next piece of the backup change information.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFBackupApplyNextChangeInfo(

	DHANDLE  ApplyInfoContext,
	DWORD  Flags,
	char *Buffer,
	DWORD  BufferSize);
```
**Description :**

This function takes and applies the next portion of the backup change 
information to the backup file.

**Parameters :**
Input :
ApplyInfoContext  -  Handle to the apply info context obtained from NSFBackupStartApplyChangeInfo.

Flags  -  Reserved, must be zero

Buffer  -  Buffer containing the backup change information.

BufferSize  -  Size of Buffer.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_CORRUPT_CHANGE_INFO - The change information is invalid or does not match the copied file.

ERR_INVALID_CHANGE_INFO_CONTEXT - The ApplyInfoContext handle is invalid.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.



**Sample Usage :**
```
   if (err = NSFBackupApplyNextChangeInfo(ApplyInfoContext,
                                          0,
                                          Buffer,
                                          FilledSize))
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
[NSFBackupEndApplyChangeInfo](/domino-c-api-docs/reference/Func/NSFBackupEndApplyChangeInfo)
[NSFBackupGetNextChangeInfo](/domino-c-api-docs/reference/Func/NSFBackupGetNextChangeInfo)
[NSFBackupStartApplyChangeInfo](/domino-c-api-docs/reference/Func/NSFBackupStartApplyChangeInfo)
---
