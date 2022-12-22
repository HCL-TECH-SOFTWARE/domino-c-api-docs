




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



**Function : Alarms**



**Alarm\_ProcessAlarm** **- Indicate
alarm has been processed.**


**----------------------------------------------------------------------------------------------------------**



**#include <alarm.h>**



STATUS
LNPUBLIC **Alarm\_ProcessAlarm(**  

      char far \*pszClientName,  

      WORD  wSnoozeMinutes,  

      UNID  EventUNID,  

      WORD  Flags**);**



**Description :**



Sent by the
client after it has processed an alarm by displaying it to the user and getting
the OK or SNOOZE from the user.


 


**Parameters :**



Input :  

pszClientName  -  Handle of the caller's name who was asked to display the
alarm.  

  

wSnoozeMinutes  -  How much to snooze the alarm by (0 if not to be snoozed)  

  

EventUNID  -  UNID of the event which is to be processed.  

  

Flags  -  Not currently used, pass in 0.  

  




Output :  

(routine)  -  NOERROR - Successfully processed the alarm.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  




 **See Also :**


**[Alarm\_RefreshAlarms](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/521B3B2B8EFF81DC852563E50045A929)**



----------------------------------------------------------------------------------------------------------


 





