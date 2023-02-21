##### Function : User Registration
##### SECReattachToRootID - Bind a sub-process to the ID file of the parent process.
---
```
#include <bsafe.h>
STATUS LNPUBLIC SECReattachToRootID(
void);
```
**Description :**

After a call to SECAttachToID, a sub-process would make this call to bind 
itself to the ID file of the parent process. 

**Parameters :**

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[SECAttachToID](/domino-c-api-docs/reference/Func/SECAttachToID)
---
