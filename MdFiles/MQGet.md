




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



**MQGet** **- Read and
dequeue a message from a message queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**



STATUS
LNPUBLIC **MQGet(**  

      MQHANDLE  Queue,  

      char far \*Buffer,  

      WORD  BufLength,  

      DWORD  Options,  

      DWORD  Timeout,  

      WORD far \*retMsgLength**);**



**Description :**



Retrieves a
message from a message queue, provided the queue is not in a QUIT state. The
message will be stored in the buffer specified in the Buffer argument.    

Note: The error code ERR\_MQ\_QUITTING indicates that the message queue is in the
QUIT state, denoting that applications that are reading the message queue
should terminate. For instance, a server addin's message queue will be placed
in the QUIT state when a "tell <addin> quit" command is input
at the console.


 


**Parameters :**



Input :  

Queue  -  The handle of the queue from which to retrieve the message.  

  

BufLength  -  Size in bytes of the buffer that will receive the message.  

  

Options  -  0 to return immediately if the message queue is empty,
MQ\_WAIT\_FOR\_MSG to wait for a message.  

  

Timeout  -  If Options is set to MQ\_WAIT\_FOR\_MSG is set, the number of
milliseconds to wait for a message before timing out. Specify 0 to wait
forever. If the message queue goes into a QUIT state before the Timeout
expires, MQGet will return immediately.  

  




Output :  

(routine)  -  NOERROR  

ERR\_MQ\_EMPTY - The specified queue is either empty or not a valid message
queue.  

ERR\_MQ\_QUITTING - The queue's quit flag is set.   

ERR\_MQ\_TIMEOUT - The queue has remained empty for more than the amount of time
specified in the Timeout argument.  

ERR\_MQ\_BFR\_TOO\_SMALL - The message being read is larger than the buffer
supplied, so the message was truncated.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

Buffer  -   Pointer to the buffer that received the message.  The message will
be truncated if the buffer is too small for the message.   

  

retMsgLength  -  The number of bytes written to the buffer.  

  




 **See Also :**


**[MQClose](MQClose.md)**


**[MQCreate](MQCreate.md)**


**[MQHANDLE](MQHANDLE.md)**


**[MQIsQuitPending](MQIsQuitPending.md)**


**[MQOpen](MQOpen.md)**


**[MQPut](MQPut.md)**


**[MQPutQuitMsg](MQPutQuitMsg.md)**


**[MQScan](MQScan.md)**


**[MQSCAN\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A08D2441ECBB08DD8525621B00482D18)**


**[MQ\_xxx (Get)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3E0ED98EFE0F295B8525621B00486DDE)**



----------------------------------------------------------------------------------------------------------


 





