




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



**EventQueueGet** **- Remove an
event from an event queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <event.h>**



STATUS
LNPUBLIC **EventQueueGet(**  

      char far \*QueueName,  

      DHANDLE far \*rethEvent**);**



**Description :**



Remove an
event from an event queue, and return a pointer to the handle of the EVENT\_DATA
structure associated with the event.  See the definition of EVENT\_DATA for more
information.


 


**Parameters :**



Input :  

QueueName  -  A far pointer to the name of the queue in which to look for
events.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - An event was found in the queue.  

ERR\_EVTQUEUE\_EMPTY - There were no events in the queue.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

rethEvent  -  A pointer to a handle to the EVENT\_DATA structure associated with
the event.    

  




 **See Also :**


**[EventDeregisterEventRequest](EventDeregisterEventRequest.md)**


**[EventGetDestName](EventGetDestName.md)**


**[EventQueueAlloc](EventQueueAlloc.md)**


**[EventQueueFree](EventQueueFree.md)**


**[EventQueuePut](EventQueuePut.md)**


**[EventRegisterEventRequest](EventRegisterEventRequest.md)**



----------------------------------------------------------------------------------------------------------


 





