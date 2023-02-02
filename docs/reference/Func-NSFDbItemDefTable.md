##### Function : Database
##### NSFDbItemDefTable - Get the database's Item Definition Table.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbItemDefTable(**

	DBHANDLE  hDB,
	ITEMDEFTABLEHANDLE far *retItemNameTable);
**Description :**
The Item Definition Table for a database contains the name and type of all the 
names and labels defined in that database.  Examples are field names, form 
names, and formula labels.  Applications can obtain a copy of the Item 
Definition Table by calling NSFDbItemDefTable, which returns a memory handle 
for the copy of the table.  The application must call OSLock to lock the table 
in memory and obtain the memory address.  The application is responsible for 
de-allocating the memory by calling OSMemFree.

For details on the structure of the Item Definition Table, please see the 
descriptions for ITEM_DEFINITION_TABLE and ITEM_DEFINITION.

    NSFDbItemDefTable is the older version of NSFDbItemDefTableExt, which is 
designed to run on pre-R5 databases.  In order to process large UNK tables, API 
developers need to use NSFDbItemDefTableExt instead of NSFDbItemDefTable.  API 
developers useNSFDbItemDefTable. 
**Parameters :**
Input :
hDB  -  A handle to a Domino database.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Operation succeeded.


retItemNameTable  -  The address of an ITEMDEFTABLEHANDLE where the handle for the Item Definition Table for the database is returned.

**Sample Usage :**
```
ITEMDEFTABLEHANDLE    table_handle;

   /* Get the Item Definition Table */
 
  if (error_status = NSFDbItemDefTable(db_handle, &table_handle))
       goto Exit;

```
**See Also :**
[ITEM_DEFINITION](D:/md_files/ITEM_DEFINITION.md)
[ITEM_DEFINITION_TABLE](D:/md_files/ITEM_DEFINITION_TABLE.md)
[NSFDbAddItemName](D:/md_files/NSFDbAddItemName.md)
---
