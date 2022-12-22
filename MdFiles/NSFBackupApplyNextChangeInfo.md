




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



**NSFBackupApplyNextChangeInfo** **- Apply the
next piece of the backup change information.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBackupApplyNextChangeInfo(**  

      DHANDLE  ApplyInfoContext,  

      DWORD  Flags,  

      char \*Buffer,  

      DWORD  BufferSize**);**



**Description :**



This
function takes and applies the next portion of the backup change information to
the backup file.


 


**Parameters :**



Input :  

ApplyInfoContext  -  Handle to the apply info context obtained from
NSFBackupStartApplyChangeInfo.  

  

Flags  -  Reserved, must be zero  

  

Buffer  -  Buffer containing the backup change information.  

  

BufferSize  -  Size of Buffer.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_CORRUPT\_CHANGE\_INFO - The change information is invalid or does not match
the copied file.  

  

ERR\_INVALID\_CHANGE\_INFO\_CONTEXT - The ApplyInfoContext handle is invalid.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  




 **Sample Usage :**


   if (err =
NSFBackupApplyNextChangeInfo(ApplyInfoContext,  

                                          0,  

                                          Buffer,  

                                          FilledSize))  

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


**[NSFBackupEndApplyChangeInfo](NSFBackupEndApplyChangeInfo.md)**


**[NSFBackupGetNextChangeInfo](NSFBackupGetNextChangeInfo.md)**


**[NSFBackupStartApplyChangeInfo](NSFBackupStartApplyChangeInfo.md)**



----------------------------------------------------------------------------------------------------------


 





