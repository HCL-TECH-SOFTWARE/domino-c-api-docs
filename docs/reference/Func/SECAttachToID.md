##### Function : User Registration
##### SECAttachToID - Bind a sub-process to the current ID file.
---
```
#include <bsafe.h>
STATUS LNPUBLIC SECAttachToID(
void);
```
**Description :**

A sub-process makes this call to bind itself to the current ID file. If its 
parent process subsequently switches to a different ID file, the sub-process' 
ID file will not be switched.

**Parameters :**

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[SECReattachToRootID](/reference/Func/SECReattachToRootID)
---
