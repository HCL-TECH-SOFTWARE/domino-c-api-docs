##### Function : Mail Gateway
##### MailGetMessageAttachmentInfo - Returns information regarding an attachment of a mail message.
---
##### #include <mailserv.h>
BOOL LNPUBLIC **MailGetMessageAttachmentInfo(**

	DHANDLE  hMessage,
	WORD  Num,
	BLOCKID far *bhItem,
	char far *FileName,
	DWORD far *FileSize,
	WORD far *FileAttributes,
	WORD far *FileHostType,
	TIMEDATE *FileCreated,
	TIMEDATE far *FileModified);
**Description :**
This function returns information regarding one of the attachments of the 
specified mail message.  The attachment of interest is specified by an index 
from 0 to the number of attachments - 1.

The BLOCKID value obtained using this function refers to memory within a note.  
This memory is managed by Domino, and should not be freed by the application.

If desired, include nsfdata.h to define ATTRIB_xxx  and HOST_xxx symbols.
**Parameters :**
Input :
hMessage  -  Open message handle.

Num  -  Attachment number (0-n).

Output :
(routine)  -  FALSE if there are no attachments; otherwise TRUE.


bhItem  -  Block ID of the attachment item.

FileName  -  File name of the attachment (null-terminated), up to MAXPATH+1(includes null terminator).  Optional - specify NULL if not to be returned.

FileSize  -  File size in bytes.  Optional - specify NULL if not to be returned.

FileAttributes  -  File attributes:  ATTRIB_READONLY, ATTRIB_PRIVATE.  Optional - specify NULL if not to be returned.

FileHostType  -  File host type:  HOST_MSDOS, HOST_MAC, HOST_UNKNOWN.  Optional - specify NULL if not to be returned.

FileCreated  -  File creation time.  Optional - specify NULL if not to be returned.

FileModified  -  File modification time.  Optional - specify NULL if not to be returned.

**Sample Usage :**
```
    for (Att = 0; MailGetMessageAttachmentInfo(hMessage, Att, 
                            &bhAttachment, OriginalFileName, 
                            NULL, NULL, NULL, NULL, NULL); Att++)
    {
        printf("\tAttachment %d = '%s'\n", Att, OriginalFileName);
    }
```
**See Also :**
[MailExtractMessageAttachment](D:/md_files/MailExtractMessageAttachment.md)
---
