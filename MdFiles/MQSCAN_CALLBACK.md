




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




**Initial Release 4.0**



**Data Type : Message Queues**



**MQSCAN\_CALLBACK** **-** Action
routine invoked by MQScan().


**----------------------------------------------------------------------------------------------------------**



**#include
<mq.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR MQSCAN\_CALLBACK)(  

   const char far \*pBuffer,  

   WORD            Length,  

   WORD            Priority,  

   void far \*      Ctx);


 


**Description :**



This type
defines the prototype of the user-written callback routine that will be invoked
by the function MQScan() for each message in a message queue. The address of a
routine with this prototype is supplied as an argument to MQScan().   

  

The Action routine may return one of the following values to affect the
behavior of MQScan:


 


NOERROR -
process the next message.


ERR\_MQSCAN\_ABORT
- return from MQScan immediately without dequeueing a message.  Note that
MQScan returns ERR\_MQSCAN\_ABORT.  

ERR\_MQSCAN\_DEQUEUE - remove the message from the queue, terminate the
enumeration, and return the current message to the caller of MQScan.  If the
Buffer is smaller than the message, MQScan can return ERR\_MQ\_BFR\_TOO\_SMALL.  

ERR\_MQSCAN\_DELETE - remove the current message from the message queue and
continue the enumeration.  

  

The arguments to the MQSCAN\_CALLBACK are as follows:  

  

pBuffer - a pointer to a buffer containing the current message.  

Length  - the length of the message in the buffer.  

Priority  - the priority of this message, from 1(highest) to MAXWORD (lowest).  

Ctx       - a pointer to user-defined data. This allows non-global data to be
shared between MQScan() and the callback function.  

  

Under Windows, the action routine must be present in an EXPORT statement in the
application's .DEF file.   

  




 **See Also :**


**[MQScan](MQScan.md)**



----------------------------------------------------------------------------------------------------------


 





