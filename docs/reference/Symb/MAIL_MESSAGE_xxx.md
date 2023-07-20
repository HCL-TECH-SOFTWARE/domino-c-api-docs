##### Symbolic Value : Mail Gateway
##### MAIL_MESSAGE_xxx - Type of message.
---
```
#include <mailserv.h>
```

**Symbolic Values :**

	MAIL_MESSAGE_UNKNOWN	  -  The message is not one of the types listed below and therefore is "unknown".

	MAIL_MESSAGE_MEMO	  -  The message is a normal memo/reply or any other type of form.

	MAIL_MESSAGE_DELIVERYREPORT	  -  The message is a successful delivery report.

	MAIL_MESSAGE_NONDELIVERYREPORT	  -  The message is an unsuccessful delivery report.

	MAIL_MESSAGE_RETURNRECEIPT	  -  The message is a return receipt.

	MAIL_MESSAGE_PHONEMESSAGE	  -  The message is a phone message.

	MAIL_MESSAGE_TRACEREPORT	  -  The message is a trace delivery report.

	MAIL_MESSAGE_NOTICE	  -  The message is a calendar and scheduling notice, such as an invitation or a confirmation.

	MAIL_MESSAGE_QUOTAREPORT	  -  This message is a quota report.


**Description :**

Each symbolic constant defines one of the well-known message types:  Memo (or Reply), Delivery Report, NonDelivery Report, Return Receipt, PhoneMessage.


**See Also :**
[MailGetMessageType](/domino-c-api-docs/reference/Func/MailGetMessageType)
---
