




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



**MQCreate** **- Create a
message queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**



STATUS
LNPUBLIC **MQCreate(**  

      const char far \*QueueName,  

      WORD  Quota,  

      DWORD  Options**);**



**Description :**



Create a
message queue with the specified name. Message queues provide Domino and Notes
applications with inter-process communication capabilities.  A subsequent call
to MQOpen is required to use this message queue.


 


**Parameters :**



Input :  

QueueName  -  A pointer to the name to be assigned to the message queue.  

  

Quota  -  Maximum number of messages that the queue may contain. Set this to
zero for the default maximum.  The default maximum number of messages that the
queue may contain is MAXWORD.  

  

Options  -  Reserved. Must be 0.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_DUPLICATE\_MQ - A message queue with the specified name already exists.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

  




 **See Also :**


**[MQClose](MQClose.md)**


**[MQGet](MQGet.md)**


**[MQHANDLE](MQHANDLE.md)**


**[MQIsQuitPending](MQIsQuitPending.md)**


**[MQOpen](MQOpen.md)**


**[MQPut](MQPut.md)**


**[MQPutQuitMsg](MQPutQuitMsg.md)**


**[MQScan](MQScan.md)**


**[MQSCAN\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A08D2441ECBB08DD8525621B00482D18)**



----------------------------------------------------------------------------------------------------------


 





