##### Function : Signal Handler
##### OSGetSignalHandler - Returns a pointer to a signal handler.
---
```
#include <ossignal.h>
OSSIGPROC LNPUBLIC OSGetSignalHandler(

	WORD  SignalHandlerID);
```
**Description :**

This function returns a pointer to a signal handler.  This function should only 
be used in a GUI environment.  Signal handlers are identified by symbolic 
values;  please see the description of "OS_SIGNAL_xxx" for a list of allowable 
values.

For example, "OSGetSignalHandler(OS_SIGNAL_MESSAGE)" will return a valid 
pointer for the message signal handler only if the function call resides in a 
DLL called by the Notes user interface.  Otherwise, NULL is returned.

**Parameters :**
Input :
SignalHandlerID  -  Signal handler ID which can be one of the OS_SIGNAL_xxx values.

Output :
(routine)  -  Pointer to a signal handler function.  If the signal handler function is not available for the given signal handler ID, NULL is returned.



**See Also :**
[IXPostMessage](/reference/Func/IXPostMessage)
[OSSetSignalHandler](/reference/Func/OSSetSignalHandler)
[OS_SIGNAL_xxx](/reference/Symb/OS_SIGNAL_xxx)
---
