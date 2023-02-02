##### Function : Mail Gateway
##### MailGetMessageSize - Returns the size of a message in bytes
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailGetMessageSize(**

	DARRAY far *MessageList,
	WORD  Message,
	DWORD far *MessageSize);
**Description :**
This functions returns the size, in bytes, of a message in a message list.
**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.


MessageSize  -  Size of message in bytes.

**See Also :**
[MailGetMessageInfo](D:/md_files/MailGetMessageInfo.md)
---
