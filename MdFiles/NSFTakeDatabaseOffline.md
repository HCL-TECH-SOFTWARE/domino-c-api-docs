




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



**NSFTakeDatabaseOffline** **- Take a
database offline to allow recovery.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFTakeDatabaseOffline(**  

      const char far \*dbPath,  

      DWORD  WaitTime,  

      DWORD  options**);**



**Description :**



This function
will stop access to a database and delete the database so that it can be
recovered.


 


**Parameters :**



Input :  

dbPath  -  Full path to the database to be taken offline.  

  

WaitTime  -  Time to wait, in milliseconds, if the database cannot be taken
offline immediately.  

  

options  -  Zero to stop access to a database and delete the database so that
it can be recovered.  See OFFLINE\_xxx for more options.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_DBINUSE - Database is being accessed by one or more processes and cannot be
taken offline.  

  

ERR\_xxx - Errors returned by lower level Notes functions.  Call to OSLoadString
to interpret the error code for display.  

  

  




 **Sample Usage :**


   if (!(err =
NSFTakeDatabaseOffline(DbPath, WaitTime, 0)))  

   {  

      sprintf(EventString, "Database file %s taken offline : ",
DbPath);  

      EventLog(LogFD, EventString);  

   }  

   else  

   {  

      sprintf(EventString,  

              "\*\*\* ERROR taking database %s offline \*\*\* (%s) : ",  

              DbPath,  

              print\_api\_error(err));  

      EventLog(LogFD, EventString);  

   }


 


 **See Also :**


**[NSFBringDatabaseOnline](NSFBringDatabaseOnline.md)**


**[OFFLINE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/77965033FE1921368525671100691F13)**



----------------------------------------------------------------------------------------------------------


 





