




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Events**



**EventRegisterEventRequest** **- Specify
the type and severity of events an event consumer will process.**


**----------------------------------------------------------------------------------------------------------**



**#include <event.h>**



STATUS
LNPUBLIC **EventRegisterEventRequest(**  

      WORD  EventType,  

      WORD  EventSeverity,  

      char far \*QueueName,  

      char far \*DestName**);**



**Description :**



This
function is called by an event consumer to specify to the Domino Event Handler
that the consumer wishes to process events of a certain type and severity.  The
consumer must call EventRegisterEventRequest once for each combination of event
type and severity in which it is interested.


 


**Parameters :**



Input :  

EventType  -  The type of event in which the event consumer is interested.  See
the definition of EVT\_xxx for permissible values.  

  

EventSeverity  -  The severity of events in which the event consumer is
interested.  See the definition of SEV\_xxx for permissible values.  

  

QueueName  -  A pointer to the name of the queue that will receive events.  

  

DestName  -  A string containing the name of a person or database to be
associated with events of this type and severity.  When an event of this type
and severity is consumed, the consumer may retrieve this name by calling the
function EventGetDestName.  If the consumer desires it  may then record the
event occurrence by either notify the person named,  or by writing to the
database named, whichever is appropriate.  

  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

  

  




 **See Also :**


**[EventQueueAlloc](EventQueueAlloc.md)**


**[EventQueueFree](EventQueueFree.md)**


**[EventQueuePut](EventQueuePut.md)**


**[EventQueueGet](EventQueueGet.md)**


**[EventDeregisterEventRequest](EventDeregisterEventRequest.md)**


**[EventGetDestName](EventGetDestName.md)**



----------------------------------------------------------------------------------------------------------


 





