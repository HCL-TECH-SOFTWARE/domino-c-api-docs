##### Function : Signal Handler
##### OSSetSignalHandler - Sets a signal handler.
---
```
#include <ossignal.h>
OSSIGPROC LNPUBLIC OSSetSignalHandler(

	WORD  SignalHandlerID,
	OSSIGPROC  Routine);
```
**Description :**

This function is used to set a user defined signal handler.

**Parameters :**
Input :
SignalHandlerID  -  Signal handler ID for the signal handler function.  Use one of the OS_SIGNAL_xxx IDs.

Routine  -  Pointer to the user defined signal handler function.  Use NULL to disable a signal handler.

Output :
(routine)  -  Pointer to the signal handler previously assigned to the specified SignalHandlerID.



**See Also :**
[OSGetSignalHandler](/reference/Func/OSGetSignalHandler)
[OS_SIGNAL_xxx](/reference/Symb/OS_SIGNAL_xxx)
---
