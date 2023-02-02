##### Function : Backup
##### NSFDoneArchivingLog - Marks the specified log file as archived.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDoneArchivingLog(**

	UNID far *LogID,
	DWORD far *LogSequenceNumber);
**Description :**
This function marks the specified log file as archived and that it is ready to 
be reused or deleted.  This function should not be called when performing an 
incremental archiving of logs.
**Parameters :**
Input :
LogID  -  UNID with the log series identifier as returned from NSFGetFirstLogToArchive or NSFGetNextLogToArchive.

LogSequenceNumber  -  The log sequence number for the archived log file as returned from NSFGetFirstLogToArchive or NSFGetNextLogToArchive.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


**Sample Usage :**
```
   if (err = NSFDoneArchivingLog(&LogId, &LogNumber))
   {
      print_api_error(err);
      break;
   }

```
**See Also :**
[NSFGetFirstLogToArchive](D:/md_files/NSFGetFirstLogToArchive.md)
[NSFGetNextLogToArchive](D:/md_files/NSFGetNextLogToArchive.md)
---
