




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



**NSFGetTransLogStyle** **- Determine
what type of transactional logging is being performed on this server.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFGetTransLogStyle(**  

      WORD far \*LogType**);**



**Description :**



This
function will determine if transactional logging has been enabled on the server
and what type of transactional logging is being performed.


 


**Parameters :**




Output :  

(routine)  -  Return status from this call indicates either success or what the
error is. The return codes include:  

  

NOERROR - If no other process is currently archiving logs.  

  

ERR\_SERVER\_NOT\_TRANSLOGGED - Transactional logging is not in effect.  

  

  

LogType  -  When Status returns NOERROR, LogType will be one of the following:
TRANSLOG\_STYLE\_CIRCULAR - for circular logging;  TRANSLOG\_STYLE\_ARCHIVE - for
archive logging  

  




 **Sample Usage :**


   if ( err =
NSFGetTransLogStyle (&LogType))  

      print\_api\_error(err);


 


      if
(LogType == TRANSLOG\_STYLE\_CIRCULAR)


      {  

         printf("\n  Transactional logging is 'CIRCULAR'.\n");  

         return 1;  

      }


 


 **See Also :**


**[TRANSLOG\_STYLE\_xxx](TRANSLOG_STYLE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





