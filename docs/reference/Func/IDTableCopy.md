##### Function : ID Table
##### IDTableCopy - Copies an ID Table.
---
```
#include <idtable.h>
STATUS LNPUBLIC IDTableCopy(

	DHANDLE  hTable,
	DHANDLE far *rethTable);
```
**Description :**

This function takes an a handle associated with an existing ID Table and 
returns a new handle of a new ID Table that is a copy of the original.  It also 
sets the IDTABLE_MODIFIED flag in the new ID Table upon successful completion.

**Parameters :**
Input :
hTable  -  A handle associated with an existing ID Table.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - If the ID Table was successfully copied.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rethTable  -  The address of a HANDLE in which the handle to the newly copied ID Table will be returned.  The caller is responsible for disposing of this memory object with IDDestroyTable() when through with it.


**Sample Usage :**
```

           if ( error_status = IDTableCopy(idtable_handle,
                                           &cpytable_handle))
               goto Exit;
           else
               cleanup_state += FREE_CPYTABLE;
     
```
**See Also :**
[IDCreateTable](/domino-c-api-docs/reference/Func/IDCreateTable)
[IDDelete](/domino-c-api-docs/reference/Func/IDDelete)
[IDDeleteAll](/domino-c-api-docs/reference/Func/IDDeleteAll)
[IDDestroyTable](/domino-c-api-docs/reference/Func/IDDestroyTable)
[IDEntries](/domino-c-api-docs/reference/Func/IDEntries)
[IDEnumerate](/domino-c-api-docs/reference/Func/IDEnumerate)
[IDInsert](/domino-c-api-docs/reference/Func/IDInsert)
[IDIsPresent](/domino-c-api-docs/reference/Func/IDIsPresent)
[IDScan](/domino-c-api-docs/reference/Func/IDScan)
[IDTableCopy](/domino-c-api-docs/reference/Func/IDTableCopy)
[IDTableSize](/domino-c-api-docs/reference/Func/IDTableSize)
---
