##### Function : Mail Gateway
##### MailIsNotToBeHeld - Determine whether a mail message is not to be held.
---
```
#include <mailserv.h>
BOOL LNPUBLIC MailIsNotToBeHeld(

	DHANDLE  hMessage);
```
**Description :**

This function returns TRUE if the MAIL_DONOTHOLD_ITEM in the specified mail 
message exists; returns FALSE otherwise.

**Parameters :**
Input :
hMessage  -  Open message handle.

Output :
(routine)  -  TRUE if mail is not to be held, FALSE otherwise.



**See Also :**
[MailOpenMessage](/reference/Func/MailOpenMessage)
[MAIL_xxx_ITEM_NUM(2)](/reference/Symb/MAIL_xxx_ITEM_NUM(2))
---
