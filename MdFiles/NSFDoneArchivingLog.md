




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



**NSFDoneArchivingLog** **- Marks the
specified log file as archived.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDoneArchivingLog(**  

      UNID far \*LogID,  

      DWORD far \*LogSequenceNumber**);**



**Description :**



This
function marks the specified log file as archived and that it is ready to be
reused or deleted.  This function should not be called when performing an
incremental archiving of logs.


 


**Parameters :**



Input :  

LogID  -  UNID with the log series identifier as returned from
NSFGetFirstLogToArchive or NSFGetNextLogToArchive.  

  

LogSequenceNumber  -  The log sequence number for the archived log file as
returned from NSFGetFirstLogToArchive or NSFGetNextLogToArchive.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  




 **Sample Usage :**


   if (err =
NSFDoneArchivingLog(&LogId, &LogNumber))  

   {  

      print\_api\_error(err);  

      break;  

   }


 


 **See Also :**


**[NSFGetFirstLogToArchive](NSFGetFirstLogToArchive.md)**


**[NSFGetNextLogToArchive](NSFGetNextLogToArchive.md)**



----------------------------------------------------------------------------------------------------------


 





