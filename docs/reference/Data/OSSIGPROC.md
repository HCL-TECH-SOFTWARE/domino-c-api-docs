##### Data Type : Signal Handler
##### OSSIGPROC - Generic pointer to a signal handler function.
---
```
#include <ossignal.h>
```
**Description :**

A variable of type OSSIGPROC is a generic pointer to a signal handler function, 
returned by OSGetSignalHandler and OSSetSignalHandler.  This pointer must be 
cast to a specific signal handler function type, OSSIGMSGPROC, OSSIGBUSYPROC, 
OSSIGBREAKPROC, or OSSIGDIALPROC to call the signal handler.

**See Also :**
[IXPostMessage](/domino-c-api-docs/reference/Func/IXPostMessage)
[OSGetSignalHandler](/domino-c-api-docs/reference/Func/OSGetSignalHandler)
[OSSetSignalHandler](/domino-c-api-docs/reference/Func/OSSetSignalHandler)
[OSSIGMSGPROC](/domino-c-api-docs/reference/Data/OSSIGMSGPROC)
[OSSIGBUSYPROC](/domino-c-api-docs/reference/Data/OSSIGBUSYPROC)
[OSSIGBREAKPROC](/domino-c-api-docs/reference/Data/OSSIGBREAKPROC)
[OSSIGDIALPROC](/domino-c-api-docs/reference/Data/OSSIGDIALPROC)
---
