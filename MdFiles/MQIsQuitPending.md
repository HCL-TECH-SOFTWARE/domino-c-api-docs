




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




**Initial Release 4.0**



**Function : Message Queues**



**MQIsQuitPending** **- Test
whether the specified message queue is in a QUIT state.**


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**



BOOL
LNPUBLIC **MQIsQuitPending(**  

      MQHANDLE  Queue**);**



**Description :**



This
function tests whether the specified message queue is in a QUIT state, and
returns TRUE if so. Otherwise, it returns FALSE.


 


**Parameters :**



Input :  

Queue  -  The handle of the message queue to check.  

  




Output :  

(routine)  -  TRUE if the specified message queue is in a QUIT state, FALSE
otherwise.  

  

  




 **See Also :**


**[MQClose](MQClose.md)**


**[MQCreate](MQCreate.md)**


**[MQGet](MQGet.md)**


**[MQHANDLE](MQHANDLE.md)**


**[MQOpen](MQOpen.md)**


**[MQPut](MQPut.md)**


**[MQPutQuitMsg](MQPutQuitMsg.md)**


**[MQScan](MQScan.md)**


**[MQSCAN\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A08D2441ECBB08DD8525621B00482D18)**



----------------------------------------------------------------------------------------------------------


 





