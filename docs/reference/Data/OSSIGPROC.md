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
[IXPostMessage](/reference/Func/IXPostMessage)
[OSGetSignalHandler](/reference/Func/OSGetSignalHandler)
[OSSetSignalHandler](/reference/Func/OSSetSignalHandler)
[OSSIGMSGPROC](/reference/Data/OSSIGMSGPROC)
[OSSIGBUSYPROC](/reference/Data/OSSIGBUSYPROC)
[OSSIGBREAKPROC](/reference/Data/OSSIGBREAKPROC)
[OSSIGDIALPROC](/reference/Data/OSSIGDIALPROC)
---
