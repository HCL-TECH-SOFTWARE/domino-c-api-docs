




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



**NSFEndArchivingLogs** **- Terminate
the archiving of transactional logs.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFEndArchivingLogs(**void**);**



**Description :**



Terminate
the archiving of transactional logs and allow other processes to archive the
log files.


 


**Parameters :**




Output :  

(routine)  -  Return status from this call indicates either success or what the
error is. The return codes include:  

  

NOERROR - Success.  No other process is currently archiving logs.  

  

ERR\_SERVER\_NOT\_TRANSLOGGED - Transactional logging is not in effect.  

  

ERR\_TRANSLOG\_NOT\_ARCHIVED - Wrong logging style (circular).  

  

ERR\_TRANSLOG\_ARCHIVE\_IN\_PROGRESS - Another process is currently archiving logs.  

  

  




 **Sample Usage :**


   if (err =
NSFEndArchivingLogs ())  

   {  

      sprintf(EventString,  

              "\*\*\* ERROR archiving logs \*\*\* (%s) : ",  

              print\_api\_error(err));  

      EventLog(LogFD, EventString);  

   }


 


 




----------------------------------------------------------------------------------------------------------


 





