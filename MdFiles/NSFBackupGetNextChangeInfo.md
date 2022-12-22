




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



**NSFBackupGetNextChangeInfo** **- Get next
portion of the backup change information.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBackupGetNextChangeInfo(**  

      DBHANDLE  hDB,  

      DHANDLE  hBackupContext,  

      DWORD  Flags,  

      char \*Buffer,  

      DWORD  BufferSize,  

      DWORD \*FilledSize**);**



**Description :**



This
function returns the next portion of the change information for the copied
database file.  The order of the returned data must be maintained when it is
passed in for application to the copied file.


 


The change
information is returned as a stream of bytes.  When the change information is
applied to the copied database file, it must be passed to
NSFBackupApplyNextChangeInfo in the same order as it is returned.


 


This
function will not return any change information unless NSFBackupStop has been
called.


 


**Parameters :**



Input :  

hDB  -  The handle to the database on which the backup is being performed.  

  

hBackupContext  -  Handle to the backup context that was obtained from
NSFBackupStart.  

  

Flags  -  Reserved, must be zero.  

  

Buffer  -  Pointer to a buffer to receive the change image information.  

  

BufferSize  -  Size of Buffer.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_NOT\_LOCAL - Database is remote.  

  

ERR\_NOT\_DOING\_BACKUP - No backup is underway.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

FilledSize  -  Pointer to a DWORD to get the amount of change information data
put in Buffer.  

  




 **Sample Usage :**


   if (err =
NSFBackupGetNextChangeInfo(hDB,  

                                        BackupContext,  

                                        0,  

                                        Buffer,  

                                        BUFFER\_SIZE,  

                                        &FilledSize))  

   {  

      print\_api\_error (err);  

      NSFBackupEndApplyChangeInfo(ApplyInfoContext, APPLYEND\_ABORT);  

      OSUnlockObject(hBuffer);  

      OSMemFree(hBuffer);  

      OSFileDelete(backup\_file);  

      OSFileClose(srcfd);  

      NSFBackupEnd(hDB, BackupContext, BACKUPEND\_ABORT);  

      NSFDbClose(hDB);  

      NotesTerm();  

      exit (EXIT\_FAILURE);  

   }


 


 **See Also :**


**[NSFBackupApplyNextChangeInfo](NSFBackupApplyNextChangeInfo.md)**


**[NSFBackupGetChangeInfoSize](NSFBackupGetChangeInfoSize.md)**


**[NSFBackupStart](NSFBackupStart.md)**


**[NSFBackupStop](NSFBackupStop.md)**



----------------------------------------------------------------------------------------------------------


 





