##### Function : ID Table
##### IDDelete - Delete an ID from the specified ID Table.
---
##### #include <idtable.h>
STATUS LNPUBLIC **IDDelete(**

	DHANDLE  hTable,
	DWORD  id,
	BOOL far *retfDeleted);
**Description :**
This function deletes an ID from the specified ID Table.  It returns a BOOL 
value in the *retfInserted parameter indicating whether or not the note ID was 
successfully deleted from the ID Table.  If the specified ID does not initially 
reside in the table, FALSE is returned in the *retfDeleted parameter.  This 
function also sets the IDTABLE_MODIFIED flag if the ID was successfully 
deleted, that is if the returned *retfDeleted value is TRUE.
**Parameters :**
Input :
hTable  -  A handle to the ID table.

id  -  The ID to delete from the ID Table.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - ID successfully deleted from the table.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


retfDeleted  -  The address of a BOOL variable in which the outcome of the call to IDDelete is placed.   TRUE - if the specified ID was deleted from the ID Table. FALSE if the ID did not previously reside in the table.  Can be NULL if no return value is required.

**See Also :**
[IDCreateTable](D:/md_files/IDCreateTable.md)
[IDInsert](D:/md_files/IDInsert.md)
---
