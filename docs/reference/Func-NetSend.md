##### Function : Network Send and Receive
##### NetSend - Sends data over a specified session.
---
##### #include <net.h>
STATUS LNPUBLIC **NetSend(**

	SESSIONID  SessionID,
	void far *Buffer,
	WORD  Length,
	WORD  Options);
**Description :**
This function sends data over a specified session.
**Parameters :**
Input :
SessionID  -   A Session ID obtained in a previous call to NetLink.

Buffer  -  Address of buffer containing data to be sent.

Length  -  Size of data to be sent.

Options  -  One of the following flags or the bitwise OR of any of the following flags:
NETOPT_SEND_NOW - indicates data should be  transmitted immediately.  Omission of this flag allows data to be buffered without necessarily being sent.   However, buffered data may be sent at anytime at the discretion of NetSend (or NetReceive).
NETOPT_FLUSH - indicates that any buffered data (to be sent or received) should be flushed  before this send commences.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Function returned successfully.
ERR_TIMEOUT - Function timed out before all the data was transmitted.  Unless this error is persistent, it should not be treated as a fatal error, and the session should be continued to be used.
ERR_xxx - STATUS returned from a lower-level C API function.  This value can be passed to OSLoadString to obtain a text string for the error.  This error should be treated as fatal and the session should be closed by the application via NetCloseSession.


**See Also :**
[NetLink](D:/md_files/NetLink.md)
[NetSetSessionMode](D:/md_files/NetSetSessionMode.md)
[NetReceive](D:/md_files/NetReceive.md)
[NetCloseSession](D:/md_files/NetCloseSession.md)
---
