##### Function : Mail Gateway
##### MailSetMessageLastError - Records text of last error when attempting to send a message.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailSetMessageLastError(**

	DARRAY far *MessageList,
	WORD  Message,
	char far *ErrorText);
**Description :**
This function records the text of the last error encountered when attempting to 
send a message.
**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

ErrorText  -  Description of the error encountered when sending the message.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**See Also :**
[](D:/md_files/.md)
---
