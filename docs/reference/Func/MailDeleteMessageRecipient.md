##### Function : Mail Gateway
##### MailDeleteMessageRecipient - Deletes a message recipient from the list of recipients.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailDeleteMessageRecipient(

	DARRAY far *MessageList,
	WORD  Message,
	WORD  RecipientNum);
```
**Description :**

This function deletes a message recipient from the list of recipients for a 
message in a message list.  This function should be called by a gateway after 
it has successfully transferred an outbound message to a recipient.  When a 
message is later "purged" and there are non-deleted recipients remaining, the 
message will be retained in the message file for future transfer by the 
gateway.

**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

RecipientNum  -  Recipient number (0-n).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[MailGetMessageRecipient](/reference/Func/MailGetMessageRecipient)
[MailPurgeMessage](/reference/Func/MailPurgeMessage)
---
