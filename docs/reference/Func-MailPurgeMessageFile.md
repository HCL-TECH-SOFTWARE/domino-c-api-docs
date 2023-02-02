##### Function : Mail Gateway
##### MailPurgeMessageFile - Purges a message file of deleted message pointers.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailPurgeMessageFile(**

	DBHANDLE  hFile);
**Description :**
This function purges a message file of deleted message pointers.  This function 
should be called once a day.
**Parameters :**
Input :
hFile  -  Open message file handle.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**See Also :**
[MailPurgeMessage](D:/md_files/MailPurgeMessage.md)
---
