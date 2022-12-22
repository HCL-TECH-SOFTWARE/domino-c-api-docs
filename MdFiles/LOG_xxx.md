




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




 


**Symbolic Value : Log**



**LOG\_xxx** **-** Public log
flags.


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**


 **Symbolic Values :**      LOG\_LEAVE\_LOCKED         -  The log entry is not written to
disk until it is completed. Can be used with LogAddText, LogAddNumberItem,
LogAddTextlistItem, LogAddTimeItem and LogEventExt.  

  

      LOG\_AUTO\_ROLLOVER      -  Auto-rollover. Can be used with LogAddText.  

  

      LOG\_TO\_CONSOLE            -  Output log entry to console. Can be used
with LogAddText.  

  

      LOG\_ADD\_TIMESTAMP       -  Add a timestamp to the message. Can be used
with LogAddText if the LogEntry parameter is LOG\_EVENT\_ENTRY and the ItemName
parameter is LOG\_ITEM\_EVENTS.  

  

      LOG\_FORMATTED\_TEXT    -  Text is already formatted. Can be used with
LogAddText.  

  

      LOG\_ITEM\_NONSUMMARY             -  Make the item non summary.  

  




**Description :**



These flags
can be used with the LogAdd functions for additional specifications about a log
entry.


 **See Also :**


**[LogAddNumberItem](LogAddNumberItem.md)**


**[LogAddText](LogAddText.md)**


**[LogAddTextlistItem](LogAddTextlistItem.md)**


**[LogAddTimeItem](LogAddTimeItem.md)**



----------------------------------------------------------------------------------------------------------


 





