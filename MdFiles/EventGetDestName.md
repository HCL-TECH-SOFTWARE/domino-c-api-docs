




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



**EventGetDestName** **- Retrieve
the user or database name associated with an event.**


**----------------------------------------------------------------------------------------------------------**



**#include <event.h>**



BOOL
LNPUBLIC **EventGetDestName(**  

      WORD  EventType,  

      WORD  EventSeverity,  

      char far \*QueueName,  

      char far \*DestName,  

      WORD  DestNameSize**);**



**Description :**



When an
event is registered, the event consumer may specify the name of a user or a
database that is to be associated with events of this particular type and
severity.  When a consumer has consumed an event, it can call EventGetDestName
to retrieve the name.  The consumer can then take whatever appropriate action
is required - it may log a message to the database named, for example.


 


**Parameters :**



Input :  

EventType  -  The type of event in which the event consumer is interested.  See
the definition of EVT\_xxx for permissible values.  

  

EventSeverity  -  The severity of the event in which the event consumer is
interested.  See the definition of SEV\_xxx for permissible values.  

  

QueueName  -  A pointer to the name of the queue receiving the events.  

  

DestNameSize  -  Size of the buffer to receive the destination name.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or
failure  

  

  

DestName  -  A string containing the name of a person or database to be
associated with events of this type and severity.  When an event of this type
and severity is consumed, the consumer may retrieve this name by calling the
function EventGetDestName.  If desired, the consumer   may then record the
event occurrence by either notifying the person named,  or by writing to the
database named, whichever is appropriate.  

  




 **See Also :**


**[EventQueueAlloc](EventQueueAlloc.md)**


**[EventQueueFree](EventQueueFree.md)**


**[EventQueuePut](EventQueuePut.md)**


**[EventQueueGet](EventQueueGet.md)**


**[EventRegisterEventRequest](EventRegisterEventRequest.md)**


**[EventDeregisterEventRequest](EventDeregisterEventRequest.md)**



----------------------------------------------------------------------------------------------------------


 





