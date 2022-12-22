




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



**NSFBringDatabaseOnline** **- Bring an
offline database online.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBringDatabaseOnline(**  

      const char far \*dbPath,  

      DWORD  options**);**



**Description :**



This
function will bring a database online for access after it has been taken
offline by NSFTakeDatabaseOffline.


 


**Parameters :**



Input :  

dbPath  -  Path to the database to be brought online.  

  

options  -  Reserved, must be zero  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions.  Call OSLoadString to
interpret the error code for display.  

  

  




 **Sample Usage :**


   if (!(err =
NSFBringDatabaseOnline(DbPath, 0)))  

   {  

      sprintf(EventString, "Database file %s brought online : ",
DbPath);  

      EventLog(LogFD, EventString);  

   }  

   else  

   {  

      sprintf(EventString,  

              "\*\*\* ERROR bringing database %s online \*\*\* (%s) : ",  

              DbPath,  

              print\_api\_error(err));  

      EventLog(LogFD, EventString);  

   }


 


 **See Also :**


**[NSFTakeDatabaseOffline](NSFTakeDatabaseOffline.md)**



----------------------------------------------------------------------------------------------------------


 





