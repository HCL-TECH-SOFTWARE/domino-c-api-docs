##### Function : Backup
##### NSFBackupSetHighWaterMark - Indicate that backup has proceeded to a certain point.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFBackupSetHighWaterMark(

	DBHANDLE  hDB,
	DHANDLE  BackupContext,
	DWORD  HighWaterMarkLow,
	DWORD  HighWaterMarkHigh);
```
**Description :**

This function indicates that the file has been recorded up to a certain point 
to reduce before-image recording cost.

**Parameters :**
Input :
hDB  -  The handle to the database on which the backup is being performed.

BackupContext  -  Handle to the backup context that was obtained from NSFBackupStart.

HighWaterMarkLow  -  Low-order 32 bits of new high water mark.

HighWaterMarkHigh  -  High-order 32 bits of new high water mark.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_NOT_LOCAL - Database is remote.

ERR_NOT_DOING_BACKUP - No backup is underway.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.



**Sample Usage :**
```
   do
   {
      ReadCount = 0;
      while (BytesLeft)
      {   
         BytesRead = min(BUFFER_SIZE, BytesLeft);
      
         if (err = OSFileRead(srcfd, Buffer, BytesRead))
            break;
         
         if ((MAXDWORD - SrcPositionLow) < BytesRead)
         {
            SrcPositionHigh++;
            SrcPositionLow = (BytesRead - (MAXDWORD - SrcPositionLow)) - 1;
         }
         else
         {
            SrcPositionLow += BytesRead;
         }
   
         /* Occassionally tell NSF that we've made progress to cut down on
            recording overhead */
         if ((++ReadCount % 10) == 0)
            NSFBackupSetHighWaterMark(hDB,
                                      BackupContext,
                                      SrcPositionLow,
                                      SrcPositionHigh);
         
         if (err = OSFileWrite(dstfd, Buffer, BytesRead))
            break;

         BytesLeft -=BytesRead;
      }

      if (FileSizeHigh > 0)
      {
         BytesLeft = MAXDWORD;
         FileSizeHigh--;
      }
      else
      {
         BytesLeft = FileSizeLow;
         FileSizeLow = 0;
      }

   } while (BytesLeft && !(err));

```
**See Also :**
[NSFBackupStart](/reference/Func/NSFBackupStart)
---
