




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




**Initial Release 6**



**Function : Backup**



**NSFRecoverDatabasesWithCallback** **- Recover
specified databases with a callback routine.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFRecoverDatabasesWithCallback(**  

      const char far \*dbNames,  

      LOGRESTORECALLBACKFUNCTION  restoreCB,  

      DWORD  Flags,  

      WORD far \*errDbIndex,  

      TIMEDATE far \*recoveryTime,  

      NOTERESTORECALLBACKFUNCTION  noteCB,  

      void far \*userParm**);**



**Description :**



This
function will apply all updates to the backup of one or more logged databases
and call the note callback routine for each note restored.


 


**Parameters :**



Input :  

dbNames  -  Pointer to a list of one or more database file names to be
recovered.  For a list containing multiple database names, each dbName must be
null terminated and there must be a second null termination after the last
dbName, to terminate the entire list.  

  

restoreCB  -  The Log Restore Callback function pointer.  This function is
called during the recovery if archived log extents are needed.  NULL should be
passed if you are not using ARCHIVE style logging.  

  

Flags  -  Specification of recovery options, see DBRECOVER\_xxx.  

  

recoveryTime  -  Only required with the DBRECOVER\_POINT\_IN\_TIME option where it
specifies the point in time to recover to.  All committed transactions
completed prior to that time are applied to the list of databases.   

  

noteCB  -   The note restore callback function pointer.  This function is
called for each note are updated during the Media Recovery process.  See
NOTERESTORECALLBACKFUNCTION.  

  

userParm  -  User parameter.  See NOTERESTORECALLBACKFUNCTION.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_RM\_LATE\_BACKUP - Backup is later than point in time specified for recovery.
You must find an earlier backup. The backups are unaffected.  

  

ERR\_RM\_RECOVER\_NONBACKUP - Attempt to recover a db using a file that was not
created with a Domino backup utility. The backups are unaffected.  

  

ERR\_RM\_LOG\_SPACE\_CRITICAL  - Circular log was getting full, recover aborted.
After this error the database cannot be recovered. the backups are corrupt.  

  

ERR\_RM\_SCAN\_IN\_PROGRESS  - A scan is already in progress, try again later.
Commonly indicates an active media recovery. The backups are unaffected.  

  

ERR\_RM\_MQ\_LOG\_ERROR - Could not retrieve log extents needed for recovery. The
backups are corrupt.  

  

ERR\_VALUE\_FLAG - Invalid parameter. The backups are unaffected.  

  

ERR\_RM\_FIXUP\_DB - Backup was from a different system, the log was reformatted
since the backup was taken or the backup is corrupt.  

  

ERR\_xxx - Errors returned by lower level functions.  Call OSLoadString to
interpret the error code for display.  

  

  

errDbIndex  -  The 1 based index of the database causing the error, if an error
is returned.  A 0 is returned if the error cannot be associated with a database. 
NULL if no database error index is desired.  

  

recoveryTime  -  When supplied, it receives the time date of the last
transaction applied to any of the databases recovered.  If NULL is provided,
nothing is returned.  

  




 **Sample Usage :**



  
if(Rflags)  

   Rflags = DBRECOVER\_ZAP\_ID;


 


  
if(RNoteInfo)  

   {


     
sprintf(EventString, "\nRecovering backup file %s with CallBack",
BUPath);  

      EventLog(LogFD, EventString);  

      err = NSFRecoverDatabasesWithCallback(BUPath, MyCallback, Rflags,
&index, NULL, NoteCallback, 0);  

   }  

   else  

   {  

        if (!Rflags)  

           sprintf(EventString, "Recovering backup file %s", BUPath);  

        else  

           sprintf(EventString, "\nRecovering backup file %s",
BUPath);  

      EventLog(LogFD, EventString);  

      err = NSFRecoverDatabases(BUPath, MyCallback, Rflags, &index, NULL);  

   }


 


   if
(!err)  

   {  

        while (BUPath[0] != '\0')  

        {  

         printf("\n Backup file %s recovered.", BUPath);  

         sprintf(EventString, "Backup file %s recovery complete",
BUPath);  

         EventLog(LogFD, EventString);  

         BUPath += strlen(BUPath) + 1;  

        }  

   }  

   else  

   {  

        while (BUPath[0] != '\0')  

        {  

           errindex++;  

           if(errindex ==index)  

           {


            
printf("\nError recovering backup file %s\n", BUPath);  

             sprintf(EventString, " \*\*\* ERROR recovering backup file %s
\*\*\* (%s)",  

                       BUPath,  

                       print\_api\_error(err));  

                       EventLog(LogFD, EventString);  

          }


         
BUPath += strlen(BUPath) + 1;  

       }  

   }


 **See Also :**


**[DBRECOVER\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/84DB8E7861AD34328525667800653496)**


**[LOGRESTORECALLBACKFUNCTION](LOGRESTORECALLBACKFUNCTION.md)**


**[NOTERESTORECALLBACKFUNCTION](NOTERESTORECALLBACKFUNCTION.md)**



----------------------------------------------------------------------------------------------------------


 





