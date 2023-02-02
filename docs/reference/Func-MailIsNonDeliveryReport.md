##### Function : Mail Gateway
##### MailIsNonDeliveryReport - Returns TRUE if message is a Non-Delivery Report.
---
##### #include <mailserv.h>
BOOL LNPUBLIC **MailIsNonDeliveryReport(**

	DHANDLE  hMessage);
**Description :**
This function returns TRUE if an open message is a Non-Delivery Report; FALSE 
if message is any other type.  This function has been superceded by the 
MailGetMessageType which returns all the message type codes.
**Parameters :**
Input :
hMessage  -  Open message handle.

Output :
(routine)  -  TRUE if message is a Non-Delivery Report; FALSE if message is any other type.


**See Also :**
[MailGetMessageType](D:/md_files/MailGetMessageType.md)
---
