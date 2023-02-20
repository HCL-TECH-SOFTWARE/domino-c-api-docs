##### Function : ID Table
##### IDDestroyTable - Free all memory associated with an ID Table.
---
```
#include <idtable.h>
STATUS LNPUBLIC IDDestroyTable(

	DHANDLE  hTable);
```
**Description :**

This function deallocates all memory associated with an ID Table. Use this 
function instead of OSMemFree to free the ID Table's memory.

**Parameters :**
Input :
hTable  -  The handle of the ID Table structure that is to be destroyed.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - If ID Table was successfully destroyed.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[IDCreateTable](/reference/Func/IDCreateTable)
---
