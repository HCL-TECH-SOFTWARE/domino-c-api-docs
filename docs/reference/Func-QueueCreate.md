##### Function : Miscellaneous
##### QueueCreate - Create a new FIFO queue
---
##### #include <misc.h>
STATUS FAR PASCAL **QueueCreate(**

	DHANDLE *rtnhandle);
**Description :**
This function will create a new FIFO queue. It  will eventually have to have 
two semaphores associated with it.  The first will be an "event" that is 
signalled once for each queue entry that is present.  At the top of the GET 
procedure, a wait-for-event operation will cause the caller to suspend until a 
queue entry is present.  The PUT procedure will signal this event whenever 
entering an entry on the queue.  The second semaphore will be a "lock" that 
prevents multiple processes calling GET from simultaneously clobbering the 
QUEUE_HEADER structure.  It will simply lock the header operations.
**Parameters :**

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rtnhandle  -  A pointer to a handle of the newely created queue

**Sample Usage :**
```
/* Start the directory search */
    
     if (error = QueueCreate(&hQueue))
      goto done_search;
```
**See Also :**
[](D:/md_files/.md)
---
