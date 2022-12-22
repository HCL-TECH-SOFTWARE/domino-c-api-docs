




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



**Symbolic Value : Alarms; Message
Queues**



**MQPREFIX\_FOR\_CLIENT** **-** Prefix for
the client name.


**----------------------------------------------------------------------------------------------------------**



**#include <alarm.h>**



**Description :**



Clients to
the alarms daemon should append the client name to the MQPREFIX\_FOR\_CLIENT
string in order to come up with a MQ Name to create before registering with the
alarms daemon for alarms.  Alarms daemon will use the name
<MQPREFIX\_FOR\_CLIENT><ClientName> as a string for opening the MQ
for the client and send alarms to it.


 **See Also :**


**[MQCreate](MQCreate.md)**


**[Alarm\_RegisterInterest](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DA1692F20B55D10D852563DC0060803E)**



----------------------------------------------------------------------------------------------------------


 





