




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



**NSFGetNextLogToArchive** **- Get the
next log file waiting to be archived.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFGetNextLogToArchive(**  

      UNID far \*LogID,  

      DWORD far \*LogNumber,  

      char far \*LogPath**);**



**Description :**



This function
checks to determine if a log file is waiting to be archived.  Whether the next
log file is waiting to be archived or not, it returns the path to the log file,
as well as the LogID and log sequence number to uniquely identify it.


 


**Parameters :**




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_NO\_TRANSLOGS\_TO\_ARCHIVE - Indicates a successful call but no log/journal
file is waiting to be archived.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

LogID  -  The log series identifier associated with this log file.  

  

LogNumber  -  Log sequence number associated with this log file.  

  

LogPath  -  Null terminated full path to the log file to be archived.  This
buffer must be at least MAXPATH+1 in length.  

  




 **Sample Usage :**


   /\* Be sure on the
first pass through to get the first archive log.


      This
ensures that the list gets reset in case this didn't leave  

      cleanly and the logger believes we are off archiving a log handed  

      top us in an earlier invocation. \*/


  

      if (FirstPass)  

      {  

         FirstPass--;  

         err = NSFGetFirstLogToArchive(&LogId, &LogNumber,
&LogPath[0]);  

      }  

      else  

         err = NSFGetNextLogToArchive(&LogId, &LogNumber,
&LogPath[0]);


 **See Also :**


**[NSFDoneArchivingLog](NSFDoneArchivingLog.md)**


**[NSFGetFirstLogToArchive](NSFGetFirstLogToArchive.md)**



----------------------------------------------------------------------------------------------------------


 





