




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



**NSFBackupStartApplyChangeInfo** **- Initiate
application of the backup change information.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBackupStartApplyChangeInfo(**  

      DHANDLE \*ApplyInfoContext,  

      char \*CopyFilePath,  

      DWORD  Flags,  

      DWORD  InfoSizeLow,  

      DWORD  InfoSizeHigh**);**



**Description :**



This
function will initiate the application of the backup change information to a
copy of a database file taken during a backup operation.  Once successfully
started NSFBackupEndApplyChangeInfo must be called to free allocated resources.


 


**Parameters :**



Input :  

  

CopyFilePath  -  Path to the file copied during the backup.  

  

Flags  -  Reserved, must be zero.  

  

InfoSizeLow  -  The low-order 32 bits of change information size.  

  

InfoSizeHigh  -  The high-order 32 bits of change information size.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

ApplyInfoContext  -  Handle to the apply info context.  

  




 **Sample Usage :**


   /\* Initiate getting
the change info \*/  

   if (err = NSFBackupStartApplyChangeInfo(&ApplyInfoContext,  

                                           backup\_file,  

                                           0,  

                                           InfoSizeLow,  

                                           InfoSizeHigh))  

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


**[NSFBackupGetChangeInfoSize](NSFBackupGetChangeInfoSize.md)**



----------------------------------------------------------------------------------------------------------


 





