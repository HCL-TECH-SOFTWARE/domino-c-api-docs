




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



**NSFDbGetLogInfo** **- Check if
database is logged.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetLogInfo(**  

      DBHANDLE  hDb,  

      DWORD  Flags,  

      BOOL \*LOGGED,  

      UNID \*LogID,  

      UNID \*DbIID,  

      DWORD \*LogExtent**);**



**Description :**



Check if
database is logged.


 


**Parameters :**



Input :  

hDb  -  Handle to database.  

  

Flags  -  Reserved, must be zero.  

  




Output :  

(routine)  -  Return status from this call indicates either success or what the
error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_NOT\_LOCAL - Database is remote.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

LOGGED  -  Pointer to BOOL.  TRUE if database is currently logged, otherwise
FALSE.  

  

LogID  -  Pointer to the UNID of a database if it is logged.  

  

DbIID  -  Pointer to the databases instance id (DBIID) of a database if it is
logged.  

  

LogExtent  -  Pointer to a DWORD set to the first log extent that will be
needed to restore the next backup taken.  

  




 **Sample Usage :**


   /\* Check to see if
DB is being logged. \*/  

   if (err = NSFDbGetLogInfo(hDB, 0L, &Logged, &LogID, &DbIID,
&LogExtent))  

   {  

      print\_api\_error (err);  

      NSFBackupEnd(hDB, BackupContext, BACKUPEND\_ABORT);  

      NSFDbClose(hDB);  

      NotesTerm();  

      exit (EXIT\_FAILURE);  

   }  

   if(!Logged)  

   {  

      printf("\n  Database '%s' is not currently logged ...\n",
path\_name);  

      printf("\n  Resulting backup file '%s' WILL NOT BE RECOVERABLE
...\n", backup\_file);  

   }


 


 




----------------------------------------------------------------------------------------------------------


 





