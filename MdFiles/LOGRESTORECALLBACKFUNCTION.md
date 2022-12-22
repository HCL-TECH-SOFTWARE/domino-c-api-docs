




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



**Data Type : Backup**



**LOGRESTORECALLBACKFUNCTION** **-** Definition
of the log restore callback function that the backup utility will have to
provide for archive logging.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR LOGRESTORECALLBACKFUNCTION)(


   UNID \*LogID,


   DWORD LogNumber,


   char
\*LogSegmentPathName);


 


**Description :**



When Archive
logging is in use, this callback function is implemented with the following
parameters:  


 


inputs:


LogID -
Pointer to the LogID identifying the log series as passed to the archive
process from NSFGetNextLogToArchive


 


LogNumber -
The log sequence number for the log file as passed to the archive process in
NSFGetNextLogToArchive.


 


LogSegmentPathName
- A pointer to a null terminated string that specifies the full path for where
the archived log file should be put.


 


outputs: 


STATUS -
Status of the call: NOERROR if the archive log file is accessible through the
LogSegmentFullPath.  Any other status indicates an error condition and the
recovery operation will be stopped.


 




----------------------------------------------------------------------------------------------------------


 





