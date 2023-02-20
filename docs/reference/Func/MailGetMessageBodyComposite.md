##### Function : Mail Gateway
##### MailGetMessageBodyComposite - Writes the composite text message body item(s) to a file.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailGetMessageBodyComposite(

	DHANDLE  hMessage,
	char far *ItemName,
	char far *OutputFileName,
	DWORD far *OutputFileSize);
```
**Description :**

This function returns the composite text (ie. rich text) message body item(s) 
and writes them to a file.  This function handles multiple items of the same 
name and therefore is not limited to 64KB of output.

**Parameters :**
Input :
hMessage  -  Open message handle.

ItemName  -  Text item name (null-terminated).  Optional - NULL is "Body".

OutputFileName  -  Output file name (null-terminated).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



OutputFileSize  -  Output file size in bytes.


**See Also :**
[MailGetMessageBody](/reference/Func/MailGetMessageBody)
[MailGetMessageBodyText](/reference/Func/MailGetMessageBodyText)
---
