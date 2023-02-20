##### Data Type : Remote LAN adapter
##### PREMOTE_LAN_SERVICE_ENTRY - Calling convention for a remote LAN service product adapter routine.
---
```
#include <net.h>
```
**Description :**

This typedef defines the interface to a remote LAN service product adapter 
general entry point routine.  This routine performs all the functions of the 
interface except for initialization.  Under Windows, the routine must be 
exported in the application's .DEF file.

This routine is called by Notes with a standard set of the first five 
paramters.  After the standard parameters, there may be additional ones 
specific to the particular action being performed, as determined by the first 
paramter, the Type parameter.

Use VARG_GET to get the arguments.

Inputs:
These are standard parameters, and must appear in the order shown below.

WORD Type Type of action to perform.  See REMOTE_LAN_SERVICE_xxx for possible 
values.

DWORD *pNativeError Place to store native error code

DWORD *pConnectionHandle 
	Address of native handle of the connection (to put to or get from, 
depending on the type)

char *pErrorBuffer Place to store error messages for display and logging by 
Notes.  Note that if type is REMOTE_LAN_SERVICE_TERMINATE this address will be 
NULL.

WORD ErrorBufferSize Size of error buffer supplied


Additional arguments -the interpretation of additonal arguments depends on the 
remote access action type:

for REMOTE_LAN_SERVICE_CONNECT:
	char *pEntryName Name of native dial information entry. 
	char *pLoginName Name to use to login to the remote network.  
	char *pPassword Password to use to login to the remote network. 
	char *pPhoneNo Phone number to dial. 
	char *pDialbackNo Phone number for the remote access server to call 
back to to complete the connection.  

for REMOTE_LAN_SERVICE_DISCONNECT:
	char *pEntryName Name of native dial information entry. 

for REMOTE_LAN_SERVICE_CHECK_CONNECTED:
	char *pEntryName Name of native dial information entry. 

for REMOTE_LAN_SERVICE_GET_EXISTING_LINKS
	None.

for REMOTE_LAN_SERVICE_TERMINATE 
	None.

for REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_INFO 
	char *pPhoneNo For return of the  phone number in the dial entry.
	char *pAreaCode For return of the  area code in the dial entry.
	char *pCountryCode For return of the country code in the dial entry.
	WORD Size of each of the previous three buffers.

for REMOTE_LAN_SERVICE_CREATE_DIAL_ENTRY_DIALOG 
	None.

for REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_LIST
	char *pReturnBuffer For return of tab-separated list of dial entry 
names, terminated by zero.
	WORD BufSize Size of storage allocated in the return buffer
	WORD *BufCount Number of characters returned, including the Null 
terminator.

Note that all strings passed to the adapter and returned from the adapter are 
stored in multibyte character (LMBCS) format. To convert these to and from a 
format acceptable to the operating system, the program must use the OSTranslate 
function.

Outputs:
pConnectionHandle Address for returning the native handle of the connection 
after a successful connect (used for call of type REMOTE_LAN_SERVICE_CONNECT)

pErrorBuffer Return error string in buffer at this address

(routine) Notes error code. The following error codes have special meaning for 
Notes dial-up connections:
NOERROR
ERR_DEVICE_IN_USE
ERR_CANCEL   (i.e. the user has aborted)
ERR_REMOTE_BUSY;
ERR_NO_ANSWER;
ERR_NO_CARRIER;
ERR_NO_DIALTONE;

For all other error condition, use:
ERR_REMOTE_LAN_ERROR.
 

**See Also :**
[PREMOTE_LAN_STATUS_CALLBACK](/reference/Data/PREMOTE_LAN_STATUS_CALLBACK)
---
