##### Function : ID Table
##### IDCreateTable - Creates an ID Table.
---
```
#include <idtable.h>
STATUS LNPUBLIC IDCreateTable(

	DWORD  Alignment,
	DHANDLE far *rethTable);
```
**Description :**

This function allocates an empty ID Table, and returns a handle to it.

ID Tables should be released with IDDestroyTable().

**Parameters :**
Input :
Alignment  -  The alignment value is used in a compression algorithm that allows continuous "adjacent" IDs to be stored in a compressed fashion.  Pass in 0 for this parameter in order for Domino or Notes to determine the proper value for this parameter.  For ID tables containing "NoteIDs", you may use the value "sizeof(NOTEID)".

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - If ID Table was successfully created.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rethTable  -  The address of a HANDLE variable in which the handle to an ID Table structure will be returned.  The caller is responsible for disposing of this memory object with IDDestroyTable when through with it.


**Sample Usage :**
```

          if (error_status = IDCreateTable(sizeof(NOTEID),
                                  &arctable_handle))
               goto Exit;
           else
               cleanup_state += FREE_ARCTABLE;

```
**See Also :**
[IDDelete](/domino-c-api-docs/reference/Func/IDDelete)
[IDDeleteAll](/domino-c-api-docs/reference/Func/IDDeleteAll)
[IDEntries](/domino-c-api-docs/reference/Func/IDEntries)
[IDEnumerate](/domino-c-api-docs/reference/Func/IDEnumerate)
[IDInsert](/domino-c-api-docs/reference/Func/IDInsert)
[IDIsPresent](/domino-c-api-docs/reference/Func/IDIsPresent)
[IDScan](/domino-c-api-docs/reference/Func/IDScan)
[IDTableCopy](/domino-c-api-docs/reference/Func/IDTableCopy)
[IDTableSize](/domino-c-api-docs/reference/Func/IDTableSize)
[IDDestroyTable](/domino-c-api-docs/reference/Func/IDDestroyTable)
---
