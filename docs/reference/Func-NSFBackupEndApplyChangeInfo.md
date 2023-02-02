##### Function : Backup
##### NSFBackupEndApplyChangeInfo - End application of the backup change information.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFBackupEndApplyChangeInfo(**

	DHANDLE  ApplyInfoContext,
	DWORD  Flags);
**Description :**
This function will terminate the application of the backup change information 
to a backup file.
**Parameters :**
Input :
ApplyInfoContext  -  Handle to the apply info context obtained from NSFBackupStartApplyChangeInfo.

Flags  -  Zero to terminate the application of the backup change information.  See APPLYEND_xxx for more options.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_INVALID_CHANGE_INFO_CONTEXT - The ApplyInfoContext handle is invalid.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


**Sample Usage :**
```
   /* Done with the backup */
   NSFBackupEndApplyChangeInfo(ApplyInfoContext,0);

```
**See Also :**
[APPLYEND_xxx](D:/md_files/APPLYEND_xxx.md)
[NSFBackupStartApplyChangeInfo](D:/md_files/NSFBackupStartApplyChangeInfo.md)
---
