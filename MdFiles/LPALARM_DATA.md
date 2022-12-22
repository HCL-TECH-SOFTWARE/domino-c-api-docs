




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



**LPALARM\_DATA** **-** Alarm
structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<alarm.h>**



**Definition :**



typedef struct {  

   TIMEDATE tmEventTime;    /\* Time for the event  \*/  

   TIMEDATE tmAlarmTime;    /\* Time for the alarm \*/  

   HANDLE   hSubject;       /\* Handle to alarm subject \*/  

   WORD     Flags;          /\* see ALARM\_DATA\_FLAG\_xxx \*/  

   UNID     EventUNID;      /\* UNID for the event note \*/  

   DHANDLE   hAlarmTuneName; /\* Tune to play \*/  

   DHANDLE   hSendMailAddr;  /\* Address to send message to \*/


} far \*LPALARM\_DATA;


 


**Description :**



Pointer to
message structure sent TO THE CLIENT, one per alarm.  There is an array of
these structures pointed to by ALARM\_MSG.


 **See Also :**


**[ALARM\_DATA](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0B2216A8BD7E3D13482573FB00322DA8)**



----------------------------------------------------------------------------------------------------------


 





