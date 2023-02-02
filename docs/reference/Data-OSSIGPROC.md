##### Data Type : Signal Handler
##### OSSIGPROC - Generic pointer to a signal handler function.
---
##### #include <ossignal.h>
**Description :**
A variable of type OSSIGPROC is a generic pointer to a signal handler function, 
returned by OSGetSignalHandler and OSSetSignalHandler.  This pointer must be 
cast to a specific signal handler function type, OSSIGMSGPROC, OSSIGBUSYPROC, 
OSSIGBREAKPROC, or OSSIGDIALPROC to call the signal handler.
**See Also :**
[IXPostMessage](D:/md_files/IXPostMessage.md)
[OSGetSignalHandler](D:/md_files/OSGetSignalHandler.md)
[OSSetSignalHandler](D:/md_files/OSSetSignalHandler.md)
[OSSIGMSGPROC](D:/md_files/OSSIGMSGPROC.md)
[OSSIGBUSYPROC](D:/md_files/OSSIGBUSYPROC.md)
[OSSIGBREAKPROC](D:/md_files/OSSIGBREAKPROC.md)
[OSSIGDIALPROC](D:/md_files/OSSIGDIALPROC.md)
---
