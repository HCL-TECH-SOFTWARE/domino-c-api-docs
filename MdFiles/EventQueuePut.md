




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



**EventQueuePut** **- Place an
event in an event queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <event.h>**



STATUS
LNPUBLIC **EventQueuePut(**  

      char far \*QueueName,  

      char far \*Originating Server,  

      WORD  Type,  

      WORD  Severity,  

      TIMEDATE far \*EventTime,  

      WORD  FormatSpecifier,  

      WORD  EventDataLength,  

      void far \*EventSpecificData**);**



**Description :**



An event
producer calls EventQueuePut to place an event in an event queue. The parameter
EventSpecificData may be used to pass user-defined data to the event consumer.  

  

Each different combination of type and severity defines a distinct event, so a
fairly large number of distinct events can be handled.  

  

Note: The names of the event type flags (EVT\_xxx) and the event severity flags
(SEV\_xxx) are descriptive of how Domino uses events. An event producer writing
to a user-defined event queue  is not required to follow this convention.   In
other words, if a user is not interested in anything relating to mail, the
event type EVT\_MAIL may be used to signal some other type of occurrence.  

  

A user might even want to re-map the event type names (defined in EVT\_xxx)  and
event severity names (defined in SEV\_xxx) to have names that are more relevant
to their tasks by doing something like:  

  

#define   User\_Defined\_Event\_1    EVT\_MAIL  

  




 


**Parameters :**



Input :  

QueueName  -  Far pointer to a null-terminated character string containing the
name of the queue that will receive the event.  Some internal queue names are
defined in EVENT\_XXXX\_QUEUE\_NAME.  

  

Originating Server  -  Far pointer to a null-terminated character string
containing the name of the server on which the event occurred.  If NULL, uses
the current server name.    

  

Type  -  The type of event.  See the definition of EVT\_xxx for a list of valid
values for this parameter.   

  

Severity  -  The severity of the event.  See the definition of SEV\_xxx for a
list of valid values for this parameter.  

  

EventTime  -  The time at which the event is generated.  

  

FormatSpecifier  -  The format of the data specific to this event.  See FMT\_XXX
for Valid format specifier flags.  

  

EventDataLength  -  The length of the data specific to this event.  

  

EventSpecificData  -  A far pointer to the first byte of data that is specific
to this event.  This data block is user-defined.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

  

  




 **See Also :**


**[EventDeregisterEventRequest](EventDeregisterEventRequest.md)**


**[EventGetDestName](EventGetDestName.md)**


**[EventQueueAlloc](EventQueueAlloc.md)**


**[EventQueueFree](EventQueueFree.md)**


**[EventQueueGet](EventQueueGet.md)**


**[EventRegisterEventRequest](EventRegisterEventRequest.md)**


**[EVENT\_XXX\_QUEUE\_NAME](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/65C2DCF646ACBE4185256AD10049586B)**


**[EVT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00EB004E00DC007F85255E8A0077FF23)**


**[FMT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C084B9CD95B090BA852562040059CC36)**


**[SEV\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00D0001E0008006E85255E8A0077FF24)**



----------------------------------------------------------------------------------------------------------


 





