




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




**Initial Release 4.5**



**Data Type : Alarms**



**ALARM\_MSG** **-** Alarms
Daemon request message


**----------------------------------------------------------------------------------------------------------**



**#include
<alarm.h>**



**Definition :**



typedef struct {  

   WORD   Type;         /\* Type of request (ALARM\_MSG\_xxx) \*/  

   WORD   Flags;        /\* Options - not used now \*/  

   WORD   wNumOfAlarms; /\* Number of alarms \*/  

   DHANDLE hAlarmsData;  /\* Handle to an array of alarms structures \*/  

} ALARM\_MSG;


 


**Description :**



Structure
defining the MQ request sent by the alarms daemon to the client who has registered
for receiving alarms.


 **See Also :**


**[MQGet](MQGet.md)**


**[Alarm\_RegisterInterest](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/DA1692F20B55D10D852563DC0060803E)**


**[Alarm\_RefreshAlarms](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/521B3B2B8EFF81DC852563E50045A929)**



----------------------------------------------------------------------------------------------------------


 





