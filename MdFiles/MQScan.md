




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



**MQScan** **- Call
action routine for each message in a message queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**



STATUS
LNPUBLIC **MQScan(**  

      MQHANDLE  Queue,  

      char far \*Buffer,  

      WORD  BufLength,  

      DWORD  Options,  

      MQSCAN\_CALLBACK  ActionRoutine,  

      void far \*Ctx,  

      WORD far \*retMsgLength**);**



**Description :**



This
function parses a message queue, calling an action routine for each message in
the queue.  If the message queue is empty, or if all messages in the queue have
been enumerated without returning an error code, MQScan returns ERR\_MQ\_EMPTY. 
In the simple case, MQScan() does not modify the contents of the queue;  by
returning the appropriate error codes to MQScan, the action routine can specify
that messages are to be removed from the queue or skipped, or that enumeration
is to be terminated immediately.  See the reference entry for MQSCAN\_CALLBACK
for more details.  

  

Note: MQScan locks out all other message queue function calls until it
completes.


 


**Parameters :**



Input :  

Queue  -  The handle of the queue to be enumerated.  

  

Buffer  -  Pointer to a buffer in which to store the retrieved message.  Set
this to NULL if you just wish to dequeue and discard a message.  

  

BufLength  -  Size in bytes of the buffer that will receive the message.  

  

Options  -  Reserved. Must be 0.  

  

ActionRoutine  -  A pointer to an action routine to be called for each message
in a message queue. The routine must match the function prototype defined my
MQSCAN\_CALLBACK.  

  

Ctx  -  A pointer to user-defined data.  This pointer is then passed to the
Action Routine.  It provides a way to pass non-global data to the Action
Routine.  

  




Output :  

(routine)  -  NOERROR  

ERR\_MQ\_EMPTY - The specified message queue is empty, not a message queue, or
all messages in the queue have been enumerated without error.  

ERR\_MQ\_QUITTING - The queue's quit flag is set, and no enumeration has
occurred.  

ERR\_MQSCAN\_ABORT - The action routine returned the error code MQSCAN\_ABORT to
MQScan. This indicates that the action routine chose to abort the enumeration
without dequeueing the current message.  

ERR\_MQ\_BFR\_TOO\_SMALL - The message being read is larger than the buffer
supplied, so the message was truncated.  

  

  

Buffer  -  Pointer to the buffer that received the message.  The message will
be truncated if the buffer is too small for the message.   

  

Ctx  -    

  

retMsgLength  -  The number of bytes written to the buffer.  

  




 **See Also :**


**[MQClose](MQClose.md)**


**[MQCreate](MQCreate.md)**


**[MQGet](MQGet.md)**


**[MQHANDLE](MQHANDLE.md)**


**[MQIsQuitPending](MQIsQuitPending.md)**


**[MQOpen](MQOpen.md)**


**[MQPut](MQPut.md)**


**[MQPutQuitMsg](MQPutQuitMsg.md)**


**[MQScan](MQScan.md)**


**[MQSCAN\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A08D2441ECBB08DD8525621B00482D18)**


**[MQ\_xxx (Get)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3E0ED98EFE0F295B8525621B00486DDE)**


**[MQ\_xxx (Open)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/67B84476621A4A5A8525667A006E85EC)**



----------------------------------------------------------------------------------------------------------


 





