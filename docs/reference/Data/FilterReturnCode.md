##### Data Type : DSAPI
##### FilterReturnCode - DSAPI Values returned from a filter event
---
```
#include <dsapi.h>
```

**Definition :**
```
typedef enum {
   kFilterNotHandled = 0,
   kFilterHandledRequest = 1,
   kFilterHandledEvent = 2,
   kFilterError = 3
} FilterReturnCode;
```

**Description :**

Return value set when the filter has completed.  For each event the filter is handling, a return value must be sent to signify further action.  The values to return are defined below.
<ul><br>
<br>
kFilterNotHandled	- signals that the filter did not process the event.<br>
kFilterHandledRequest	- signals that the http request has completly been processed by the filter. A response has already been sent to the client, and the http stack must terminate the processing of the request.<br>
kFilterHandledEvent	- signals that the event has been handled by the filter, but further processing is to take place to completly service the http request.<br>
kFilterError	- signals that the filter encountered and error while processing the event. In this case the http stack is to stop processing the request, and send an appropriate error response to the user.</ul>



**See Also :**
[DSAPI_xxx](/domino-c-api-docs/reference/Symb/DSAPI_xxx)
---
