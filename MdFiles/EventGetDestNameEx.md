




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




**Initial Release 5.0.3**



**Function : Events**



**EventGetDestNameEx** **- Retrieve
the user or database name associated with an event.**


**----------------------------------------------------------------------------------------------------------**



**#include <event.h>**



BOOL
LNPUBLIC **EventGetDestNameEx(**  

      WORD  EventType,  

      WORD  EventSeverity,  

      char \*ErrorCode,  

      char \*ErrorText,  

      char \*QueueName,  

      char \*DestName,  

      WORD  DestNameSize**);**



**Description :**



When an
event is registered, the event consumer may specify the name of a user or a
database that is to be associated with events of this particular type,
severity, code and text.  When a consumer has consumed an event, it can call
EventGetDestNameEx to retrieve the name.  The consumer can then take whatever
appropriate action is required - it may log a message to the database named,
for example.


 


**Parameters :**



Input :  

EventType  -  The type of event in which the event consumer is interested.  See
the definition of EVT\_xxx for permissible values.  

  

EventSeverity  -  The severity of the event in which the event consumer is
interested.  See the definition of SEV\_xxx for permissible values.  

  

ErrorCode  -  Pointer to the error code associated with the given event (see
EVENT\_DATA.)  

  

ErrorText  -  Pointer to the event specific data associated with the given
event (see EVENT\_DATA.)  

  

QueueName  -  A pointer to the name of the queue receiving the events.  

  

DestNameSize  -  Size of the buffer to receive the destination name.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or
failure.  

  

  

DestName  -  A string containing the name of a person or database to be
associated with events of this type and severity.  When an event of this type
and severity is consumed, the consumer may retrieve this name by calling the
function EventGetDestNameEx.  If desired, the consumer   may then record the
event occurrence by either notifying the person named,  or by writing to the
database named, whichever is appropriate.  

  




 **See Also :**


**[EventGetDestName](EventGetDestName.md)**


**[EventQueueGet](EventQueueGet.md)**


**[EVENT\_DATA](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/179DC79145140DED85256A2A0065E34F)**


**[EVT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00EB004E00DC007F85255E8A0077FF23)**


**[SEV\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00D0001E0008006E85255E8A0077FF24)**



----------------------------------------------------------------------------------------------------------


 





