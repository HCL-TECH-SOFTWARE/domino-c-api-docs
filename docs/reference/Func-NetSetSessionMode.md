##### Function : Network Send and Receive
##### NetSetSessionMode - Sets various modes for a network session.
---
##### #include <net.h>
STATUS LNPUBLIC **NetSetSessionMode(**

	SESSIONID  SessionID,
	WORD  Options,
	DWORD  SendTimeout,
	DWORD  ReceiveTimeout,
	WORD  NumBuffers,
	WORD  BufferSize);
**Description :**
This function sets various parameters and modes for sessions, as well as 
preallocating a network buffer.  If this function is called more than once (for 
a given session), the previous allocated  buffer is deallocated and a new one 
allocated.  This means that any bytes being buffered for sends or receives are 
lost.
**Parameters :**
Input :
SessionID  -  A Session ID obtained in a previous call to NetLink.

Options  -  One of the following:
NETOPT_STREAM_MODE - Places session into stream mode.
0 - Places session into message mode.

SendTimeout  -  Default send timeout (10 ms. units).

ReceiveTimeout  -  Default receive timeout (10 ms. units).

NumBuffers  -  Number of network buffers to preallocate.

BufferSize  -  Default buffer size (0 indicates use a driver selected size).

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Function returned successfully.
ERR_xxx - STATUS returned from a lower-level C API function.  This value can be passed to OSLoadString to obtain a text string for the error.  This error should be treated as fatal and the session should be closed by the application via NetCloseSession.


**See Also :**
[NetLink](D:/md_files/NetLink.md)
[NetSend](D:/md_files/NetSend.md)
[NetReceive](D:/md_files/NetReceive.md)
[NetCloseSession](D:/md_files/NetCloseSession.md)
---
