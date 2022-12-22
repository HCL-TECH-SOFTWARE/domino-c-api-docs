




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



**MQClose** **- Close a
message queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**



STATUS
LNPUBLIC **MQClose(**  

      MQHANDLE  Queue,  

      DWORD  Options**);**



**Description :**



This
function will decrement a message queue's reference count. If the reference
count equals 0, the memory for the message queue is freed.


 


**Parameters :**



Input :  

Queue  -  The handle of the message queue that is to be closed.  

  

Options  -  Reserved. Must be 0.  

  




Output :  

(routine)  -  NOERROR  

ERR\_MQ\_EMPTY - The MQHANDLE passed into this routine was not a valid MQHANDLE.  

  

  




 **See Also :**


**[MQCreate](MQCreate.md)**


**[MQGet](MQGet.md)**


**[MQHANDLE](MQHANDLE.md)**


**[MQIsQuitPending](MQIsQuitPending.md)**


**[MQOpen](MQOpen.md)**


**[MQPut](MQPut.md)**


**[MQPutQuitMsg](MQPutQuitMsg.md)**


**[MQScan](MQScan.md)**


**[MQSCAN\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A08D2441ECBB08DD8525621B00482D18)**



----------------------------------------------------------------------------------------------------------


 





