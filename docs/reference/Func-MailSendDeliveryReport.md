##### Function : Mail Gateway
##### MailSendDeliveryReport - Sends a Delivery Report back to a message's originator.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailSendDeliveryReport(**

	DARRAY far *MessageList,
	WORD  Message,
	WORD  RecipientNums,
	WORD far *RecipientNumList);
**Description :**
This function sends a Delivery Report back to a message's originator.  The 
report can name one or more message recipients.  A gateway should send a 
Delivery Report when it determines that the message has been delivered to a 
foreign mail recipient's "mailbox" and the message contained 
DELIVERY_REPORT_CONFIRMED in the Report field.
**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

RecipientNums  -  Count of recipient numbers in RecipientNumList.

RecipientNumList  -  Pointer to an array of recipient numbers indicating the undeliverable.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**See Also :**
[MailSendNonDeliveryReport](D:/md_files/MailSendNonDeliveryReport.md)
---
