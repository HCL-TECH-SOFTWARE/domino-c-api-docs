##### Symbolic Value : Remote LAN adapter
##### REMOTE_LAN_xxx - Type of action that a remote LAN adapter can specify to a Notes status callback routine.
---
```
#include <net.h>
```

**Symbolic Values :**

	REMOTE_LAN_INIT_THREAD	  -  Make sure this thread is known to Notes. Before any status messages can be displayed by Notes by a thread that is different from the one Notes called the adapter on, you need to call the Notes remote LAN adapter status callback routine with this Action.

	REMOTE_LAN_TERM_THREAD	  -  Decrement the Notes use count on this thread. If a remote LAN adapter called the Notes remote LAN adapter status callback routine with the Action parameter set to REMOTE_LAN_INIT_THREAD, once the connection has been made or if the connection failed, you must call the Notes remote LAN adapter status callback with the Action parameter set to this value. The thread init and thread term actions may be called multiple times for a thread, but the number of termination calls must match the number of init calls before the thread is terminated.

	REMOTE_LAN_DISPLAY_STATUS	  -  Map a Notes status message and display it. The status message is specified in the StatusCode parameter of the Notes remote LAN adapter callback routine and is one of the REMOTE_LAN_STATUS_xxx values.

	REMOTE_LAN_CHECK_ABORT	  -  Check for a user abort condition. The Notes remote LAN adapter callback routine returns TRUE if the operation should continue and FALSE if the user asked for an abort (e.g. ctl+break for a PC, or command-period for a Macintosh).

	REMOTE_LAN_DISPLAY_ERR0R_TEXT	  -  Display an error message in the language provided by the remote LAN service. The error string is specified in the pErrText parameter of the Notes remote LAN adapter callback routine.


**Description :**

These values are used by a remote LAN adapter in calls to the Notes remote LAN adapter status callback routine in order to specify what type of action is to be performed by Notes.


**See Also :**
[PREMOTE_LAN_STATUS_CALLBACK](/domino-c-api-docs/reference/Data/PREMOTE_LAN_STATUS_CALLBACK)
[REMOTE_LAN_STATUS_xxx](/domino-c-api-docs/reference/Symb/REMOTE_LAN_STATUS_xxx)
---
