##### Symbolic Value : Remote LAN adapter
##### REMOTE_LAN_STATUS_xxx - Status codes that a remote LAN adapter can pass to a Notes status callback routine.
---
```
#include <net.h>
```

**Symbolic Values :**

	REMOTE_LAN_STATUS_STARTING_CONNECTION	  -  Calling remote LAN.

	REMOTE_LAN_STATUS_PHYSICALLY_CONNECTED	  -  Connected to remote LAN.

	REMOTE_LAN_STATUS_AUTHENTICATING	  -  Authenticating with remote LAN.

	REMOTE_LAN_STATUS_AUTHENTICATED	  -  Authenticated.

	REMOTE_LAN_STATUS_WAITING_FOR_CALLBACK	  -  Waiting for call back.

	REMOTE_LAN_STATUS_LINK_ESTABLISHED	  -  Remote LAN link established.

	REMOTE_LAN_STATUS_LINK_FAILED	  -  Link to remote LAN failed.

	REMOTE_LAN_STATUS_HANGING_UP	  -  Terminating remote LAN link.

	REMOTE_LAN_STATUS_HANGUP_COMPLETE	  -  Remote LAN link terminated.


**Description :**

These status codes are used by a remote LAN adapter in calls to the Notes remote LAN adapter status callback routine when the Action parameter is specified as REMOTE_LAN_DISPLAY_STATUS.  The remote LAN adapter specifies one of these status codes to the Notes remote LAN adapter callback routine in order for Notes to display the status information. 


**See Also :**
[PREMOTE_LAN_STATUS_CALLBACK](/domino-c-api-docs/reference/Data/PREMOTE_LAN_STATUS_CALLBACK)
---
