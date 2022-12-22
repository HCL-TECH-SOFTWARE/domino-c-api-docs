




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



**NSFBackupGetChangeInfoSize** **- Get size
of the backup change information.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBackupGetChangeInfoSize(**  

      DBHANDLE  hDB,  

      DHANDLE  hBackupContext,  

      DWORD  Flags,  

      DWORD \*InfoSizeLow,  

      DWORD \*InfoSizeHigh**);**



**Description :**



This
function will return the total size in bytes of the change information for the
copied database file.


 


This
function will not return any change information unless NSFBackupStop has been
called.


 


**Parameters :**



Input :  

hDB  -  The handle to the database on which the backup is being performed.  

  

hBackupContext  -  Handle to the backup context that was obtained from
NSFBackupStart.  

  

Flags  -  Reserved, must be zero.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_NOT\_LOCAL - Database is remote.  

  

ERR\_NOT\_DOING\_BACKUP - No backup is underway.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

InfoSizeLow  -  Pointer to DWORD to get the low 32 bits of change information
size.  

  

InfoSizeHigh  -  Pointer to DWORD to get the high 32 bits of change information
size.  

  




 **Sample Usage :**


   /\* Get the change
info size \*/  

   if (err = NSFBackupGetChangeInfoSize(hDB,  

                                        BackupContext,  

                                        0,  

                                        &InfoSizeLow,  

                                        &InfoSizeHigh))  

   {  

      print\_api\_error (err);  

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


**[NSFBackupStart](NSFBackupStart.md)**


**[NSFBackupStartApplyChangeInfo](NSFBackupStartApplyChangeInfo.md)**


**[NSFBackupStop](NSFBackupStop.md)**



----------------------------------------------------------------------------------------------------------


 





