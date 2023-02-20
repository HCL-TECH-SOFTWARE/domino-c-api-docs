##### Function : Miscellaneous
##### QueueDelete - Delete a queue object.
---
```
#include <misc.h>
STATUS FAR PASCAL QueueDelete(

	DHANDLE  queue);
```
**Description :**

Delete a queue object, usually after all its contents have been fetched using a 
loop calling QueueGet.  QueueDelete can be called before a queue has been fully 
processed, but it will return ERR_QUEUE_NOT_EMPTY if so.

**Parameters :**
Input :
queue  -  The handle to the queue which is to be deleted

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_QUEUE_NOT_EMPTY - The queue is not empty.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```
if (err = NSFSearchStart(search_db, fhandle, NULL, NULL,
           qhandle, flags, noteclass,
           NOTE_CLASS_NONE, granularity,
           since, &until, &shandle))
      {
      QueueDelete(qhandle);
      goto done;
      }
```
**See Also :**
---
