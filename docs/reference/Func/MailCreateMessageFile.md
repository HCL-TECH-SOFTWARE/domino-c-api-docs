##### Function : Mail Gateway
##### MailCreateMessageFile - Creates and opens a new gateway message file.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailCreateMessageFile(

	char far *FileName,
	char far *TemplateFileName,
	char far *Title,
	DBHANDLE far *rethFile);
```
**Description :**

This function creates and opens a new gateway message file.  This function 
should be called by the gateway to create a new message file when it begins 
execution for the first time.  Use MailCloseMessageFile to close the message 
file handle and deallocate the memory associated with it.

The access control list of the new message file is created with Default set to 
Depositor access and the local server and the value of the Admin notes.ini 
variable set to Manager access.

**Parameters :**
Input :
FileName  -  Message file pathname string pointer (null-terminated).

TemplateFileName  -  Message file template pathname string pointer (null-terminated).

Title  -  Title string pointer (null-terminated).  NULL if template title is to be used.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


rethFile  -  Message file handle.


**See Also :**
[MailCloseMessageFile](/reference/Func/MailCloseMessageFile)
---
