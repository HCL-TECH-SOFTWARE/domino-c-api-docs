




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



**EventQueueFree** **- Destroy
an event queue.**


**----------------------------------------------------------------------------------------------------------**



**#include <event.h>**



void
LNPUBLIC **EventQueueFree(**  

      char far \*QueueName**);**



**Description :**



Destroy the
event queue with the given name and deallocate the memory associated with it. 
EventQueueFree is called at shutdown time by each event consumer.


 


**Parameters :**



Input :  

QueueName  -  pointer to a null-terminated character string containing the name
of the queue to be destroyed.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

  

  




 **See Also :**


**[EventQueueAlloc](EventQueueAlloc.md)**


**[EventQueuePut](EventQueuePut.md)**


**[EventQueueGet](EventQueueGet.md)**


**[EventRegisterEventRequest](EventRegisterEventRequest.md)**


**[EventDeregisterEventRequest](EventDeregisterEventRequest.md)**


**[EventGetDestName](EventGetDestName.md)**



----------------------------------------------------------------------------------------------------------


 





