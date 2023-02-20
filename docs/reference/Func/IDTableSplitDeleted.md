##### Function : ID Table
##### IDTableSplitDeleted - Splits out deleted noteIDs from the source table and returns the deleted IDs as an output.
---
```
#include <idtable.h>
STATUS IDTableSplitDeleted(

	DHANDLE  hSrcTable,
	DWORD  splitMask,
	DHANDLE*rethDeletedTable);
```
**Description :**

This API retrieves deleted noteIDs from the source table as an output. It 
splits the given ID table and extracts the deleted ID by splitting the table by 
applying mask on every ID in the split table. Caller has to   free the output 
of resulting table "rethDeletedTable". 

If we set mask variable as '0' it doesn't mask any noteIDs from the deleted 
table. See the following sample output:
NoteID from Deleted Table 80008110
NoteID from Deleted Table 80009110
No. of entries in Deleted Table: 2 

If we set mask  variable as '1' it will mask all note IDs from the deleted 
table. See the following sample output: 
NoteID from Deleted Table 0
No. of entries in Deleted Table: 1 

If we set the given input note ID as mask, it doesn't mask given input note ID 
from the deleted table and remaining note ids will be masked from deleted table.
NoteID from Deleted Table 80008110
No. of entries in Deleted Table: 1

**Parameters :**
Input :
hSrcTable  -  table to split into 2 

splitMask  -  A mask which is applied to every ID in SplitTable.

Output :
(routine)  -  On invalid or NULL arguments, returns ERR_MISC_INVALID_ARGS error, on successful conversion returns NOERROR. On all other error returns NOTES Error.  


rethDeletedTable  -  resulting table (including RRV_DELETED ID if present) and all IDs after. 


**Sample Usage :**
```
DHANDLE hTableSrc = NULLHANDLE;
DHANDLE hTableDel = NULLHANDLE;
NOTEID Noteid1 = 0x00009110;
NOTEID Noteid2 = 0x00008110;
if (error = IDCreateTable(0, &hTableSrc))
{
PRINTLOG("\nError : Source table creation failed .\n\n");
return error;
}
if (error = IDInsert(hTableSrc, Noteid1, NULL))
{
PRINTLOG("\nError : Inserting NoteID %d into source table failed.\n\n", 
(int)Noteid1);
IDDestroyTable(hTableDel);
IDDestroyTable(hTableSrc);
return error; 
} if (error = IDInsert(hTableSrc, Noteid2, NULL))
{
PRINTLOG("\nError : Inserting NoteID %d into source table failed.\n\n", 
(int)Noteid2);
IDDestroyTable(hTableDel);
IDDestroyTable(hTableSrc);
return error;
}
if (error = IDTableSplitDeleted(hTableSrc, 0, &hTableDel))
{
IDDestroyTable(hTableSrc);
IDDestroyTable(hTableDel);
return error;
}
```
**See Also :**
---
