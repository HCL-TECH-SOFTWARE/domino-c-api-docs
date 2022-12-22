




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 5.0**



**Function : Backup**



**NSFBackupStart** **- Initiate
backup of a database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBackupStart(**  

      DBHANDLE  hDB,  

      DWORD  Flags,  

      DHANDLE \*BackupContext,  

      DWORD \*FileSizeLow,  

      DWORD \*FileSizeHigh**);**



**Description :**



This
function will initiate the backup of a database and return a backup context to
the caller.  The backup facility is only supported for local databases.


 


**Parameters :**



Input :  

hDB  -  The handle to the database that you want to back up.  

  

Flags  -  Reserved, must be zero.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_NOT\_LOCAL - Database is remote.  

  

ERR\_CANT\_BACKUP\_DURING\_COMPACT - In place compacting of database is in
progress, backup is not possible.  

  

ERR\_BACKUP\_ALREADY\_IN\_PROGRESS - A backup is already underway, another cannot
be started.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

BackupContext  -  Pointer to a handle that will be set to the backup context to
be used for subsequent calls.  

  

FileSizeLow  -  Pointer to a DWORD that will be set to the low-order 32 bits of
file size as of the start of the backup.  

  

FileSizeHigh  -  Pointer to a DWORD that will be set to the high-order 32 bits
of file size as of the start of the backup.  

  




 **Sample Usage :**


   /\* Start recording
changes to the file at the NSF level \*/  

   if (err = NSFBackupStart(hDB,  

                            0L,  

                            &BackupContext,  

                            &FileSizeLow,  

                            &FileSizeHigh))  

   {  

      print\_api\_error (err);  

      NSFDbClose(hDB);  

      NotesTerm();  

      exit (EXIT\_FAILURE);  

   }


 


 **See Also :**


**[NSFBackupEnd](NSFBackupEnd.md)**


**[NSFBackupGetChangeInfoSize](NSFBackupGetChangeInfoSize.md)**


**[NSFBackupGetNextChangeInfo](NSFBackupGetNextChangeInfo.md)**


**[NSFBackupSetHighWaterMark](NSFBackupSetHighWaterMark.md)**


**[NSFBackupStop](NSFBackupStop.md)**



----------------------------------------------------------------------------------------------------------


 





