##### Function : Miscellaneous
##### QueueGet - Routine to get an entry from the head of the queue.
---
```
#include <misc.h>
STATUS FAR PASCAL QueueGet(

	DHANDLE  queue,
	DHANDLE *rtnhandle);
```
**Description :**

Routine to get an entry from the head of the queue.

**Parameters :**
Input :
queue  -  The handle to the queue which is to be parsed.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rtnhandle  -  A pointer to the handle of the head of the queue.


**Sample Usage :**
```
DHANDLE hSearchEntry;
    
      err = QueueGet(qhandle,&hSearchEntry);
      if (err) break;
```
**See Also :**
---
