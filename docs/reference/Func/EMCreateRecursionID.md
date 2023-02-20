##### Function : Extension Manager
##### EMCreateRecursionID - Returns a recursion ID for use with EMRegister().
---
```
#include <extmgr.h>
STATUS LNPUBLIC EMCreateRecursionID(

	WORD far *retRecursionID);
```
**Description :**

The recursion ID is used in Domino or Notes core to resolve any recursion 
issues that might arise from the callback function making a call to core 
functions (for example, calling NSFDbOpen() from an extension manager hook for 
NSFDbOpen()).

If a recursion ID of zero is passed to EMRegister(), Domino or Notes will not 
check for recursion.  The extension manager hook will always be called for that 
function.

In order to prevent recursion, a recursion ID must be obtained by calling 
EMCreateRecursionID() and this recursion ID must be passed to EMRegister().  
Domino or Notes will check before calling the extension manager hook to ensure 
that the current thread has not already called the hook.  If it has, the call 
to the extension manager hook is skipped.

**Parameters :**

Output :
(routine)  -  
NOERROR
ERR_ILLEGALEXT


retRecursionID  -  Returns recursion ID to be passed to EMRegister.


**See Also :**
[EMRegister](/reference/Func/EMRegister)
[EMHANDLER](/reference/Data/EMHANDLER)
---
