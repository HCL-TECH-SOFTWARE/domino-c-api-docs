##### Symbolic Value : Remote LAN adapter
##### REMOTE_LAN_SERVICE_xxx - Type of action to be performed by a remote LAN adapter.
---
```
#include <net.h>
```

**Symbolic Values :**

	REMOTE_LAN_SERVICE_CONNECT	  -  Dial the connection, or skip dialing if already connected.

	REMOTE_LAN_SERVICE_DISCONNECT	  -  Hang up the connection, or skip hanging up if the connection is already terminated.

	REMOTE_LAN_SERVICE_TERMINATE	  -  Perform any needed one-time termination functions. This is called once for each process that called the remote LAN adapter's initialization function. You do not need to perform any action if no action is needed by the dialing software.

	REMOTE_LAN_SERVICE_CHECK_CONNECTED	  -  Check whether a connection already exists. If currently connected, return the value 1 in the location pointed to by the second call argument , return a value of 0 if the connection does not exist. Always return NOERROR as the function value. Note that this is a change from Version 0 of the Remote LAN interface, where the connection value was returned as the function value.

	REMOTE_LAN_SERVICE_GET_EXISTING_LINKS	  -  Return (if possible) a list of existing connections to this remote LAN adapter program. This list is a single string with entries separated by tab characters. Before creating this string, the adapter program must convert the names from the native character set to Lotus multibyte character set (LMBCS).

	REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_INFO	  -  Return the phone number, area code and country code from the native dial entry information. This is not supported by Version 0 of the Remote LAN interface. It is supported by Version 1 of the Remote LAN interface.

	REMOTE_LAN_SERVICE_CREATE_DIAL_ENTRY	  -  Not used

	REMOTE_LAN_SERVICE_CREATE_DIAL_ENTRY_DIALOG	  -  Causes the native dialer to bring up a dialog which allows the user to create a dial information entry. This is not supported by Version 0 of the Remote LAN interface. It is supported by Version 1 of the Remote LAN interface.

	REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_LIST	  -  Return a tab-separated list of native dial entries. This is not supported by Version 0 of the Remote LAN interface. It is supported by Version 1 of the Remote LAN interface.


**Description :**

These values specify what action is to be performed by a remote LAN adapter.  Domino and Notes calls the remote LAN adapter's general entry point function with the Type parameter set to one of these values.  See the chapter in the <i>Lotus C API User Guide</i>, Remote LAN Access Product Adapter, for details.


**See Also :**
[PREMOTE_LAN_SERVICE_ENTRY](/domino-c-api-docs/reference/Data/PREMOTE_LAN_SERVICE_ENTRY)
---
