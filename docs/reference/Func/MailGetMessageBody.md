##### Function : Mail Gateway
##### MailGetMessageBody - Returns a copy of the Body field text from an open message.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailGetMessageBody(

	DHANDLE  hMessage,
	DHANDLE far *hBody,
	DWORD far *BodyLength);
```
**Description :**

This function returns a copy of the text of the Body field from an open message.

The Body field is converted to a series of 78 or less character lines.  Each 
line is terminated by a null character ('\0'). 

This function can only handle plain text and can only return the text when it 
is 64 KB or less.  See the MailGetMessageBodyText function for handling text 
greater than 64KB.

**Parameters :**
Input :
hMessage  -  Open message handle.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


hBody  -  Body text handle.

BodyLength  -  Length of text in body (0-64K).


**See Also :**
[MailGetMessageBodyText](/reference/Func/MailGetMessageBodyText)
[MailGetMessageBodyComposite](/reference/Func/MailGetMessageBodyComposite)
---
