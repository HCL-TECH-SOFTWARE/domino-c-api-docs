##### Function : Mail Gateway
##### MailGetMessageOriginatorDomain - Gets message originator domain string.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailGetMessageOriginatorDomain(**

	DARRAY far *MessageList,
	WORD  Message,
	char far *OriginatorDomain,
	WORD  OriginatorDomainSize,
	WORD far *OriginatorNameLength);
**Description :**
This function parses the specified message to yield the originator's domain.  
The message is parsed to yield the rightmost domain in the "@" separated list.
**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

OriginatorDomainSize  -  Size of originator domain string buffer.

Output :
(routine)  -   Return status from the call -- indicates either success (NOERROR) or what the error is.



OriginatorDomain  -  Pointer to returned originator domain string (not null-terminated).  It is up to the caller to allocate space for this buffer.

OriginatorNameLength  -  Pointer to returned string lengh of the originator domain.

**See Also :**
[MailGetMessageOriginator](D:/md_files/MailGetMessageOriginator.md)
---
