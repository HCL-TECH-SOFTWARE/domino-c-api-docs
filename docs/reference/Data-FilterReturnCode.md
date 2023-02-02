##### Data Type : DSAPI
##### FilterReturnCode - DSAPI Values returned from a filter event
---
##### #include <dsapi.h>
**Description :**
Return value set when the filter has completed.  For each event the filter is 
handling, a return value must be sent to signify further action.  The values to 
return are defined below.

kFilterNotHandled - signals that the filter did not process the event.
kFilterHandledRequest - signals that the http request has completly been 
processed by the filter. A response has already been sent to the client, and 
the http stack must terminate the processing of the request.
kFilterHandledEvent - signals that the event has been handled by the filter, 
but further processing is to take place to completly service the http request.
kFilterError - signals that the filter encountered and error while processing 
the event. In this case the http stack is to stop processing the request, and 
send an appropriate error response to the user.
**See Also :**
[DSAPI_xxx](D:/md_files/DSAPI_xxx.md)
---
