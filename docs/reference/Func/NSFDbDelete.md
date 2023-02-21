##### Function : Database
##### NSFDbDelete - Delete a database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbDelete(

	cost char far *PathName);
```
**Description :**

This function deletes a specified Domino database using the path specification 
provided.

**Parameters :**
Input :
PathName  -  The address of a text buffer containing a database name or alternately, a full network path specification to the database built with OSPathNetConstruct.  The database file name should be a null-terminated string.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - database successfully deleted.
ERR_NOACCESS - You are not authorized to perform that operation
ERR_NOEXIST -  File does not exist
ERR_DRIVE_NOT_READY - Drive is not ready
ERR_LOCK - File cannot be shared while in use by another process
ERR_IOERROR - I/O data error
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```

   if (cleanup_state & DELETE_DST_DB)  /* delete incomplete work */
       if (cleanup_status = NSFDbDelete(dst_name))
       {
           OSLoadString(0, cleanup_status, cleanup_msg, LINEOTEXT-1);
           printf("\nCleanup Error: %s\n", cleanup_msg);
       }

```
**See Also :**
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
[OSPathNetConstruct](/domino-c-api-docs/reference/Func/OSPathNetConstruct)
---
