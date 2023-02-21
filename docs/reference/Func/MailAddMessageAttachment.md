##### Function : Mail Gateway
##### MailAddMessageAttachment - Adds a file attachment to a message.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailAddMessageAttachment(

	DHANDLE  hMessage,
	char far *FileName,
	char far *OriginalFileName);
```
**Description :**

This function adds a file attachment to a message.  This function is usually 
used by gateways to handle inbound messages with file attachments.

**Parameters :**
Input :
hMessage  -  Open message handle.

FileName  -  The address of a null-terminated file name string which contains the fully qualified file path specification for the file being attached.

OriginalFileName  -  The address of a null-terminated string containing a filename that will be stored internally with the attachment, displayed with the atttachment icon when the document is viewed in the Notes user interface, and subsequently used when selecting which attachment to Extract or Detach and what path to create for an Extracted file.  It is recommended that you use a meaningful filename as opposed to a random one whenever possible.  If attaching mulitiple files that have the same filename but different content to a single document, make sure this variable is unique in each call to MailAddMessageAttachment().

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[MailCreateMessage](/domino-c-api-docs/reference/Func/MailCreateMessage)
[MailExtractMessageAttachment](/domino-c-api-docs/reference/Func/MailExtractMessageAttachment)
[MailGetMessageAttachmentInfo](/domino-c-api-docs/reference/Func/MailGetMessageAttachmentInfo)
---
