##### Function : Mail Gateway
##### MailCloseMessageFile - Closes an open message file.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailCloseMessageFile(

	DBHANDLE  hFile);
```
**Description :**

This function closes an open message file.

**Parameters :**
Input :
hFile  -  Open message file handle.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[MailOpenMessageFile](/reference/Func/MailOpenMessageFile)
[MailCreateMessageFile](/reference/Func/MailCreateMessageFile)
---
