##### Function : Mail Gateway
##### MailExtractMessageAttachment - Extracts a file attachment from a message into a disk file.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailExtractMessageAttachment(

	DHANDLE  hMessage,
	BLOCKID  bhItem,
	char far *FileName);
```
**Description :**

This function extracts a file attachment from a message into a disk file.  The 
file is usually a temporary file used to contain the file data while the 
gateway transfers the data to the recipients.

If an attachment has been compressed, it will be decompressed as it is 
extracted.

Since a gateway never has access to a recipient's private key, if an attachment 
has been encrypted, it cannot be extracted.  If an attachment is encrypted, the 
ERR_NOEXTRACT_ENCRYPTED error is returned.

The modification date on the file is set to the attached file's modification 
date.

**Parameters :**
Input :
hMessage  -  Open message handle.

bhItem  -  Block ID of the attachment (returned by MailGetAttachmentInfo)

FileName  -  File name string pointer (null-terminated).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[MailGetMessageAttachmentInfo](/reference/Func/MailGetMessageAttachmentInfo)
---
