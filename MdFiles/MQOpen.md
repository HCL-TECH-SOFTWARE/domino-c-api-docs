




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



**MQOpen** **- Open a
message queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**



STATUS
LNPUBLIC **MQOpen(**  

      const char far \*QueueName,  

      DWORD  Options,  

      MQHANDLE far \*RetQueue**);**



**Description :**



Open a
message queue, get a handle to it, and increment the queue's reference counter.
The handle is used by the functions that write to and read from the message
queue.


 


**Parameters :**



Input :  

QueueName  -  The name of the queue that is to be opened.  

  

Options  -   Optional MQOpen options.  Should be 0 or see MQ\_xxx (MQOpen -
Options) for possible values.  

  




Output :  

(routine)  -    

NOERROR  

ERR\_NO\_SUCH\_MQ - No message queue with the specified name exists.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

  

RetQueue  -  A pointer to message queue's handle.  

  




 **See Also :**


**[MQClose](MQClose.md)**


**[MQCreate](MQCreate.md)**


**[MQGet](MQGet.md)**


**[MQHANDLE](MQHANDLE.md)**


**[MQIsQuitPending](MQIsQuitPending.md)**


**[MQPut](MQPut.md)**


**[MQPutQuitMsg](MQPutQuitMsg.md)**


**[MQScan](MQScan.md)**


**[MQSCAN\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A08D2441ECBB08DD8525621B00482D18)**


**[MQ\_xxx (Open)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/67B84476621A4A5A8525667A006E85EC)**



----------------------------------------------------------------------------------------------------------


 





