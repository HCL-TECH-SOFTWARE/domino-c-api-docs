##### Symbolic Value : Signal Handler
##### OS_SIGNAL_xxx - Signal handler IDs used by OSGetSignalHandler and OSSetSignalHandler.
---
```
#include <ossignal.h>
```

**Symbolic Values :**

	OS_SIGNAL_MESSAGE	  -  Return address of the function that can be used to place a text string in the message/status area of the Status Bar of the workstation's main window. See OSSIGMSGPROC for the prototype of this function.

	OS_SIGNAL_BUSY	  -  Return address of the function that paints a busy indicator on the screen. See OSSIGBUSYPROC for the prototype of this function.

	OS_SIGNAL_CHECK_BREAK	  -  Returns a pointer to a function that checks to see if the user cancelled some I/O. See OSSIGBREAKPROC for the prototype of this function.

	OS_SIGNAL_DIAL	  -  Return address of the function that prompts the user to dial a remote system. Notes calls the signal handler just prior to initiating the process of an external dial. See OSSIGDIALPROC for the prototype of this function.

	OS_SIGNAL_PROGRESS	  -  Put up and manipulate the system wide progress indicator.

	OS_SIGNAL_REPL	  -  Signal the replication state.


**Description :**

Type of signal handler used by OSGetSignalHandler and OSSetSignalHandler to obtain address of the function that handles the signal.


**See Also :**
[IXPostMessage](/domino-c-api-docs/reference/Func/IXPostMessage)
[OSSIGMSGPROC](/domino-c-api-docs/reference/Data/OSSIGMSGPROC)
[OSSIGBUSYPROC](/domino-c-api-docs/reference/Data/OSSIGBUSYPROC)
[OSSIGBREAKPROC](/domino-c-api-docs/reference/Data/OSSIGBREAKPROC)
[OSSIGDIALPROC](/domino-c-api-docs/reference/Data/OSSIGDIALPROC)
[OSGetSignalHandler](/domino-c-api-docs/reference/Func/OSGetSignalHandler)
[OSSetSignalHandler](/domino-c-api-docs/reference/Func/OSSetSignalHandler)
---
