##### Function : ID Table
##### IDTableIntersect - Returns the ID's that are common to two ID Tables.
---
##### #include <idtable.h>
STATUS  LNPUBLIC **IDTableIntersect(**

	DHANDLE  hSrc1Table,
	DHANDLE  hSrc2Table,
	DHANDLE *rethDstTable);
**Description :**
This function creates the intersection of two ID Tables.  The resulting table 
contains those IDs that are common to both source tables.
**Parameters :**
Input :
hSrc1Table  -  Handle to the first of two ID Tables that will be compared.

hSrc2Table  -  Handle to the second of two ID Tables that will be compared.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Success.

ERR_IDTABLE_INVALID - An invalid ID Table was specified.

ERR_xxx - Errors returned by lower level functions. Call to OSLoadString and display/log the error for the user.


rethDstTable  -  Pointer to the handle of the resulting ID Table.  This table contains the IDs that are common to hSrc1Table and hSrc2Table.  If the handle of the resulting table is specified as NULLHANDLE, then the resulting table will be created and populated.  Otherwise the specified resulting table will be replaced.  You need to make sure that the handle pointed to by rethDstTable is either NULLHANDLE or a valid handle to an ID Table.  You also need to detroy the resulting table when done with it with IDDestroyTable.

**See Also :**
[IDCreateTable](D:/md_files/IDCreateTable.md)
[IDAreTablesEqual](D:/md_files/IDAreTablesEqual.md)
[IDDestroyTable](D:/md_files/IDDestroyTable.md)
---
