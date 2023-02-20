##### Function : ID Table
##### IDDeleteTable - Delete a given set of IDs from an ID Table.
---
```
#include <idtable.h>
STATUS LNPUBLIC IDDeleteTable(

	DHANDLE  hTable,
	DHANDLE  hIDsToDelete);
```
**Description :**

This function deletes the IDs specified in one ID Table from a source ID 
Table.  If an ID that is specified as "to be deleted" does not exist in the 
source ID Table, it is ignored.

This function will set the  IDTABLE_MODIFIED flag if at least one ID was 
deleted from the ID Table. 

This function is similar to IDDelete.  IDDelete can delete only one ID at a 
time.  This function can be used to delete a set of IDs.

**Parameters :**
Input :
hTable  -  Handle to the source ID Table.  This table will not contain those IDs specified in the hIDsToDelete table upon successful completion of this function.

hIDsToDelete  -  Handle to the table of IDs to be deleted from  hTable.  The resulting table will not contain IDs that are in this table.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Success.

ERR_xxx - Errors returned by lower level functions. Call to OSLoadString and display/log the error for the user.


hTable  -  The resulting table.  The source ID Table is replaced by the resulting ID Table.


**See Also :**
[IDCreateTable](/reference/Func/IDCreateTable)
[IDInsertTable](/reference/Func/IDInsertTable)
[IDDelete](/reference/Func/IDDelete)
---
