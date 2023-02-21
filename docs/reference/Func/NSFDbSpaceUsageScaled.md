##### Function : Database
##### NSFDbSpaceUsageScaled - Returns information about the usage of space in a database in granules.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbSpaceUsageScaled(

	DBHANDLE  hDB,
	DWORD far *retAllocatedGranules,
	DWORD far *retFreeGranules,
	DWORD far *retGranularity);
```
**Description :**

This function returns the number of granules allocated, the number of granules 
free, and the granularity size in a specified database.
Granules relate to the number of bits in space allocation instead of the number 
of bytes.  By multiplying the granules allocated by the granularity size, and 
the granules free by the granularity size, the result will be in bytes 
allocated and free.  Please see the function NSFDbSpaceUsage for more 
information.

**Parameters :**
Input :
hDB  -  Handle to the database.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - success

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that  it is best to use the code in a call to OSLoadString and display/log the error for the user.


retAllocatedGranules  -  Pointer to the returned number of granules allocated in the database.

retFreeGranules  -  Pointer to the returned number of granules free in the database.

retGranularity  -  Pointer to the granularity size of the database.


**See Also :**
[NSFDbSpaceUsage](/domino-c-api-docs/reference/Func/NSFDbSpaceUsage)
---
