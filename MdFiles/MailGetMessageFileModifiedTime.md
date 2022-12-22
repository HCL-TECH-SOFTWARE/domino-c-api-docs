




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Mail Gateway**



**MailGetMessageFileModifiedTime** **- Returns
the timestamp of last modification time of a message file.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageFileModifiedTime(**  

      DBHANDLE  hFile,  

      TIMEDATE far \*retModifiedTime**);**



**Description :**



This function
returns the timestamp of the last modification time of the message file.  It
can be used by a gateway to determine if new messages have been added to the
file since the last time it checked.


 


**Parameters :**



Input :  

hFile  -  Open message file handle.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

retModifiedTime  -  Time/date of last modification of message file (e.g.
time/date last message was added/deleted.  

  




 **See Also :**


**[NSFDbModifiedTime](NSFDbModifiedTime.md)**


**[MailGetMessageItemTimeDate](MailGetMessageItemTimeDate.md)**



----------------------------------------------------------------------------------------------------------


 





