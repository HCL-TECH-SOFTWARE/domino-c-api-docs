##### Function : Log
##### LogCloseActivityStream - Close an activity logging stream
---
```
#include <log.h>
STATUS LNPUBLIC LogCloseActivityStream(

	void *pStreamCtx);
```
**Description :**

This function closes an activity logging stream, and free its associated 
resources

**Parameters :**
Input :
pStreamCtx  -  The stream context created by LogOpenActivityStream

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully closed activity stream.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[LogOpenActivityStream](/reference/Func/LogOpenActivityStream)
---
