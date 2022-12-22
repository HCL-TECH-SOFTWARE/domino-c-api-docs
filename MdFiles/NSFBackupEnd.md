




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



**NSFBackupEnd** **-
Deallocate the backup context.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBackupEnd(**  

      DBHANDLE  hDB,  

      DHANDLE  BackupContext,  

      DWORD  Options**);**



**Description :**



This
function will deallocate the backup context that was obtained from
NSFBackupStart once all recorded updates on the file should have been
processed.


 


**Parameters :**



Input :  

hDB  -  The handle to the database that whose backup is to be terminated.  

  

BackupContext  -  Handle to the backup context that was obtained from
NSFBackupStart.  

  

Options  -  Zero to deallocate the backup context once all recorded updates
have been processed.  See BACKUPEND\_xxx for more options.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_NOT\_LOCAL - Database is remote.  

  

ERR\_NOT\_DOING\_BACKUP - No backup is underway.  

  

ERR\_xxx - Errors returned by lower level functions.  Call OSLoadString to
interpret the error code for display.  

  

  




 **Sample Usage :**


   /\* Done with the
backup \*/  

   NSFBackupEnd(hDB, BackupContext, 0);


 


 **See Also :**


**[BACKUPEND\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/1A4B6D6DF2A7F324852567110068CDEB)**


**[NSFBackupStart](NSFBackupStart.md)**


**[NSFBackupStop](NSFBackupStop.md)**



----------------------------------------------------------------------------------------------------------


 





