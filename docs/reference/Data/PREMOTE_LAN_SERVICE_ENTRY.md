##### Data Type : Remote LAN adapter
##### PREMOTE_LAN_SERVICE_ENTRY - Calling convention for a remote LAN service product adapter routine.
---
```
#include <net.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR PREMOTE_LAN_SERVICE_ENTRY)(
   VARARG_PTR Ap);
```

**Description :**

This typedef defines the interface to a remote LAN service product adapter general entry point routine.  This routine performs all the functions of the interface except for initialization.  Under Windows, the routine must be exported in the application's .DEF file.
<ul><br>
<br>
This routine is called by Notes with a standard set of the first five paramters.  After the standard parameters, there may be additional ones specific to the particular action being performed, as determined by the first paramter, the Type parameter.<br>
<br>
Use VARG_GET to get the arguments.<br>
<br>
Inputs:<br>
These are standard parameters, and must appear in the order shown below.</ul>

<ul>
<ul>WORD Type	Type of action to perform.  See REMOTE_LAN_SERVICE_xxx for possible values.<br>
<br>
DWORD *pNativeError	Place to store native error code<br>
<br>
DWORD *pConnectionHandle	<br>
	Address of native handle of the connection (to put to or get from, depending on the type)<br>
<br>
char *pErrorBuffer	Place to store error messages for display and logging by Notes.  Note that if type is REMOTE_LAN_SERVICE_TERMINATE this address will be NULL.<br>
<br>
WORD ErrorBufferSize	Size of error buffer supplied<br>
</ul>
</ul>

<ul>
<ul><b>Additional arguments -</b>the interpretation of additonal arguments depends on<b> </b>the remote access action type:<br>
<br>
for REMOTE_LAN_SERVICE_CONNECT:<br>
	char *pEntryName	Name of native dial information entry. <br>
	char *pLoginName	Name to use to login to the remote network. 	<br>
	char *pPassword	Password to use to login to the remote network.	<br>
	char *pPhoneNo	Phone number to dial.	<br>
	char *pDialbackNo	Phone number for the remote access server to call back to to complete the connection. 	<br>
<br>
for REMOTE_LAN_SERVICE_DISCONNECT:<br>
	char *pEntryName	Name of native dial information entry. <br>
<br>
for REMOTE_LAN_SERVICE_CHECK_CONNECTED<b>:</b><br>
	char *pEntryName	Name of native dial information entry. <br>
<br>
for REMOTE_LAN_SERVICE_GET_EXISTING_LINKS<br>
	None.<br>
<br>
for REMOTE_LAN_SERVICE_TERMINATE <br>
	None.<br>
<br>
for REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_INFO <br>
	char *pPhoneNo	For return of the  phone number in the dial entry.<br>
	char *pAreaCode	For return of the  area code in the dial entry.<br>
	char *pCountryCode	For return of the country code in the dial entry.<br>
	WORD	Size of each of the previous three buffers.<br>
<br>
for REMOTE_LAN_SERVICE_CREATE_DIAL_ENTRY_DIALOG <br>
	None.<br>
<br>
for REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_LIST<br>
	char *pReturnBuffer	For return of tab-separated list of dial entry names, terminated by zero.<br>
	WORD BufSize	Size of storage allocated in the return buffer<br>
	WORD *BufCount	Number of characters returned, including the Null terminator.</ul>
</ul>
<br>
Note that all strings passed to the adapter and returned from the adapter are stored in multibyte character (LMBCS) format. To convert these to and from a format acceptable to the operating system, the program must use the OSTranslate function.
<ul><br>
Outputs:
<ul>pConnectionHandle	Address for returning the native handle of the connection after a successful connect (used for call of type REMOTE_LAN_SERVICE_CONNECT)<br>
<br>
pErrorBuffer	Return error string in buffer at this address<br>
<br>
(routine)	Notes error code. The following error codes have special meaning for Notes dial-up connections:
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>NOERROR<br>
ERR_DEVICE_IN_USE<br>
ERR_CANCEL   (i.e. the user has aborted)<br>
ERR_REMOTE_BUSY;<br>
ERR_NO_ANSWER;<br>
ERR_NO_CARRIER;<br>
ERR_NO_DIALTONE;</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>

<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>For all other error condition, use:<br>
ERR_REMOTE_LAN_ERROR<font color="#FF0000">.</font></ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
 


**See Also :**
[PREMOTE_LAN_STATUS_CALLBACK](/domino-c-api-docs/reference/Data/PREMOTE_LAN_STATUS_CALLBACK)
---
