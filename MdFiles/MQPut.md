




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



**MQPut** **- Adds a
message to the specified message queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**



STATUS
LNPUBLIC **MQPut(**  

      MQHANDLE  Queue,  

      WORD  Priority,  

      char far \*Buffer,  

      WORD  Length,  

      DWORD  Options**);**



**Description :**



This
function adds a message to the specified message queue. The message will be
placed in the queue according to the value of its priority argument - higher
priority messages will be enqueued ahead of lower priority messages.  

  

If the queue is full or in a QUIT state, the message will not be put in the
queue, and the function will return an appropriate error code.


 


**Parameters :**



Input :  

Queue  -  The handle of the queue that will receive the message.  

  

Priority  -  The priority of this message. See xxxPRIORITY.  

  

Buffer  -  A pointer to the buffer containing the message.  Maximum buffer
length is MQ\_MAX\_MSGSIZE.  

  

Length  -  Length of the message in bytes.  

  

Options  -  Reserved. Must be 0.  

  




Output :  

(routine)  -  NOERROR  

ERR\_MQ\_EMPTY - The specified queue is either empty or not a valid message
queue.  

ERR\_MQ\_QUITTING - The queue's quit flag is set.  

ERR\_MQ\_EXCEEDED\_QUOTA - The message queue is full and cannot take another
message.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[MQClose](MQClose.md)**


**[MQCreate](MQCreate.md)**


**[MQGet](MQGet.md)**


**[MQHANDLE](MQHANDLE.md)**


**[MQIsQuitPending](MQIsQuitPending.md)**


**[MQOpen](MQOpen.md)**


**[MQPutQuitMsg](MQPutQuitMsg.md)**


**[MQScan](MQScan.md)**


**[MQ\_MAX\_MSGSIZE](MQ_MAX_MSGSIZE.md)**


**[MQ\_xxx (Get)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3E0ED98EFE0F295B8525621B00486DDE)**


**[MQ\_xxx (Open)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/67B84476621A4A5A8525667A006E85EC)**



----------------------------------------------------------------------------------------------------------


 





