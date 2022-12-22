




<!--
 /\* Font Definitions \*/
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




**Initial Release 4.5**



**Symbolic Value : Alarms**



**ALARM\_MSG\_xxx** **-** ALARM\_MSG -
Type


**----------------------------------------------------------------------------------------------------------**



**#include <alarm.h>**


 **Symbolic Values :**      ALARM\_MSG\_PENDING\_ALARMS   -  Message sent when there are
'past alarms' - alarms prior to today which haven't been displayed to the user.
Client will get a buffer with all the past alarms and a count of how many
alarms there are. All the alarms have the structure defined in this file.  

  

      ALARM\_MSG\_NEW\_ALARM            -  Sent by the alarms daemon when there is
a new alarm which needs to be displayed.  

  

      ALARM\_MSG\_IS\_TERMINATING     -  Sent by the alarms daemon to all clients
before it terminates.  

  




**Description :**



Messages
sent by the alarms daemon in the MQ of the client.  Client should periodically
check it's queue in order to receive these and do the appropriate tasks.


 **See Also :**


**[ALARM\_MSG\_xxx](ALARM_MSG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





