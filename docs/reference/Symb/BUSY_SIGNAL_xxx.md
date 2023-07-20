##### Symbolic Value : Signal Handler
##### BUSY_SIGNAL_xxx - Busy signal handler specific definitions.
---
```
#include <ossignal.h>
```

**Symbolic Values :**

	BUSY_SIGNAL_FILE_INACTIVE	  -  Remove the "File Activity" indicator

	BUSY_SIGNAL_FILE_ACTIVE	  -  Display the "File Activity" indicator (not supported on all platforms)

	BUSY_SIGNAL_NET_INACTIVE	  -  Remove the "Network Activity" indicator.

	BUSY_SIGNAL_NET_ACTIVE	  -  Display the "Network Activity" indicator.

	BUSY_SIGNAL_POLL	  -  Display the "Poll" indicator.

	BUSY_SIGNAL_WAN_SENDING	  -  Display the "Wan Sending" indicator.

	BUSY_SIGNAL_WAN_RECEIVING	  -  Display the "Wan Receiving" indicator.


**Description :**

These symbolic constants identify the type of busy signal indicator that is to be painted on the screen when the busy signal handler function (OS_SIGNAL_BUSY) is called.


**See Also :**
[OSSIGBUSYPROC](/domino-c-api-docs/reference/Data/OSSIGBUSYPROC)
[OS_SIGNAL_xxx](/domino-c-api-docs/reference/Symb/OS_SIGNAL_xxx)
---
