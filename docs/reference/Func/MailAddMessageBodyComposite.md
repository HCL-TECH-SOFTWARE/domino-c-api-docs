##### Function : Mail Gateway
##### MailAddMessageBodyComposite - Adds a composite text body item(s) from a file to a message.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailAddMessageBodyComposite(

	DHANDLE  hMessage,
	char far *ItemName,
	char far *InputFileName);
```
**Description :**

This function adds a composite text (ie. rich text) body item(s) from a file to 
a message.  This function creates multiple items of the same name and therefore 
is not limited to 64KB of input.

**Parameters :**
Input :
hMessage  -  Open message handle.

ItemName  -  Text item name (null-terminated).  Optional - NULL is "Body".

InputFileName  -  Input file name string (null-terminated).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[MailGetMessageBodyComposite](/reference/Func/MailGetMessageBodyComposite)
---
