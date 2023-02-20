##### Function : Mail Gateway
##### MailSendNonDeliveryReport - Sends a Non-Delivery Report back to a message's originator.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailSendNonDeliveryReport(

	DARRAY far *MessageList,
	WORD  Message,
	WORD  RecipientNums,
	WORD far *RecipientNumList,
	char far *ReasonText,
	WORD  ReasonTextLength);
```
**Description :**

This function sends a Non-Delivery Report back to a message's originator.  The 
report can name one or more message recipients.  A gateway should send a 
Non-Delivery Report when it encounters an unrecoverable failure attempting to 
transfer or deliver the message to the recipients.

The report includes a list of the recipients that were undeliverable, text 
describing the failure, and all the original fields in the message.

**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

RecipientNums  -  Count of recipient numbers in RecipientNumList.

RecipientNumList  -  Pointer to an array of recipient numbers indicating the undeliverable recipients.

ReasonText  -  Reason text string pointer.

ReasonTextLength  -  Reason text string length.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[MailSendDeliveryReport](/reference/Func/MailSendDeliveryReport)
---
