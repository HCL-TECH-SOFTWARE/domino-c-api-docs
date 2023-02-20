##### Function : ID Table
##### IDTableReplaceExtended - Replace an ID table with the contents of another ID table.
---
```
#include <idtable.h>
STATUS IDTableReplaceExtended(

	DHANDLE  hSrcTable,
	DHANDLE  hDstTable);
```
**Description :**

"This routine is called to replace the ID table content from another ID table. 
It validates the ID table headers for the new format and replaces the content 
accordingly.

**Parameters :**
Input :
hSrcTable  -  Database Handle for ID table to copy. .

hDstTable  -  Database Handle for ID table to be replaced. 

Output :
(routine)  -  On invalid or NULL arguments, returns ERR_MISC_INVALID_ARGS error, on successful conversion returns NOERROR. On all other error returns NOTES Error.  



**Sample Usage :**
```
DHANDLE hTableDst = NULLHANDLE;
DHANDLE hTableSrc = NULLHANDLE;
 if (error = IDCreateTable(0, &hTableDst))
{
printf("\nError : Destination table creation failed .\n\n");
return error;
}

if (error = IDCreateTable(0, &hTableSrc))
{
printf("\nError : Source table creation failed .\n\n");
IDDestroyTable(hTableDst);
return error;
} 
 //Insert noteIDs into source and destination table
 if (error = IDTableReplaceExt(hTableSrc, hTableDst))
{
PrintAPIError(error);
IDDestroyTable(hTableSrc);
IDDestroyTable(hTableDst);
return error;
}

```
**See Also :**
---
