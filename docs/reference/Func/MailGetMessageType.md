##### Function : Mail Gateway
##### MailGetMessageType - Returns the type of an open message.
---
```
#include <mailserv.h>
WORD LNPUBLIC MailGetMessageType(

	DHANDLE  hMessage);
```
**Description :**

This function returns the type of an open message.  This function determines if 
the message is one of the well-known message types:  Memo (or Reply), Delivery 
Report, NonDelivery Report, Return Receipt, PhoneMessage.

If the message is not one of the above, then the message type is "unknown".  
This function uses the Form field to determine the message type.

**Parameters :**
Input :
hMessage  -  Open message handle

Output :
(routine)  -  Type of message, which can be one of MAIL_MESSAGE_xxx.



**See Also :**
[MAIL_MESSAGE_xxx](/reference/Symb/MAIL_MESSAGE_xxx)
---
