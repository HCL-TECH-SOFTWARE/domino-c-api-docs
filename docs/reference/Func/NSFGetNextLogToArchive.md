##### Function : Backup
##### NSFGetNextLogToArchive - Get the next log file waiting to be archived.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFGetNextLogToArchive(

	UNID far *LogID,
	DWORD far *LogNumber,
	char far *LogPath);
```
**Description :**

This function checks to determine if a log file is waiting to be archived.  
Whether the next log file is waiting to be archived or not, it returns the path 
to the log file, as well as the LogID and log sequence number to uniquely 
identify it.

**Parameters :**

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_NO_TRANSLOGS_TO_ARCHIVE - Indicates a successful call but no log/journal file is waiting to be archived.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


LogID  -  The log series identifier associated with this log file.

LogNumber  -  Log sequence number associated with this log file.

LogPath  -  Null terminated full path to the log file to be archived.  This buffer must be at least MAXPATH+1 in length.


**Sample Usage :**
```
   /* Be sure on the first pass through to get the first archive log.
      This ensures that the list gets reset in case this didn't leave
      cleanly and the logger believes we are off archiving a log handed
      top us in an earlier invocation. */

      if (FirstPass)
      {
         FirstPass--;
         err = NSFGetFirstLogToArchive(&LogId, &LogNumber, &LogPath[0]);
      }
      else
         err = NSFGetNextLogToArchive(&LogId, &LogNumber, &LogPath[0]);
```
**See Also :**
[NSFDoneArchivingLog](/reference/Func/NSFDoneArchivingLog)
[NSFGetFirstLogToArchive](/reference/Func/NSFGetFirstLogToArchive)
---
