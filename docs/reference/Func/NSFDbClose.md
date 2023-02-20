##### Function : Database
##### NSFDbClose - Closes a database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbClose(

	DBHANDLE  hDB);
```
**Description :**

This subroutine closes a previously opened database.  It is important to close 
databases when you are through using them, since the close operation flushes 
data structures to disk and cleans up memory space.

Note that databases which have been closed by the C API may still be shown as 
"in use" by the host operating system.  This can happen, for example, on a 
server when a database has been opened by a server add-in program.

**Parameters :**
Input :
hDB  -  The handle to the database that you want to close.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully closed the database.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**Sample Usage :**
```
/* Normal cleanup */
if (error_status = NSFDbClose(db_handle_src))
  goto Exit;
else
  cleanup_state -= CLOSE_SRC_DB;
```
**See Also :**
[NSFDbOpen](/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/reference/Func/NSFDbOpenExtended)
---
