##### Function : Mail Gateway
##### MailFreeMessageList - Unlocks and frees an in-memory message list.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailFreeMessageList(**

	DHANDLE  hMessageList,
	DARRAY far *MessageList);
**Description :**
This function unlocks and frees an in-memory message list.
**Parameters :**
Input :
hMessageList  -  Message list handle.

MessageList  -  Message list pointer.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**See Also :**
[MailCreateMessageList](D:/md_files/MailCreateMessageList.md)
---
