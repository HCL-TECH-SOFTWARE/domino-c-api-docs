##### Function : ID Table
##### IDInsertTable - Insert a given set of IDs into an ID Table.
---
```
#include <idtable.h>
STATUS LNPUBLIC IDInsertTable(

	DHANDLE  hTable,
	DHANDLE  hIDsToAdd);
```
**Description :**

This function inserts a given set of IDs from one ID Table into a source ID 
Table.  If an ID in the given set of IDs to be inserted already exists in the 
source ID Table, it is ignored.

The IDTABLE_MODIFIED flag is set if at least one ID was inserted into the ID 
Table. 

ID Tables are ordered by ID value. IDInsert stores the ID in the table 
according to its value.

This function is similar to IDInsert.  IDInsert can insert only one ID at a 
time.  This function can be used to insert a set of IDs.

**Parameters :**
Input :
hTable  -  Handle to the source ID Table.  This table will contain these IDs as well as the additional IDs upon successful completion of this function.

hIDsToAdd  -  Handle to the table of IDs to be inserted into  hTable. 

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Success.

ERR_IDTABLE_INVALID - An invalid ID Table was specified.

ERR_xxx - Errors returned by lower level functions. Call to OSLoadString and display/log the error for the user.


hTable  -  The resulting table.  The source ID Table is replaced by the resulting ID Table.


**See Also :**
[IDCreateTable](/reference/Func/IDCreateTable)
[IDDeleteTable](/reference/Func/IDDeleteTable)
[IDInsert](/reference/Func/IDInsert)
---
