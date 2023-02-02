##### Function : ID Table
##### IDAreTablesEqual - Determine whether two ID Tables contain the same contents.
---
##### #include <idtable.h>
BOOL	LNPUBLIC **IDAreTablesEqual(**

	DHANDLE  hSrc1Table,
	DHANDLE  hSrc2Table);
**Description :**
This function compares two ID Tables and returns TRUE if they contain the same 
contents.  Otherwise, FALSE is returned.  

You can pass in NULLHANDLE for the handle of either of the ID Tables.  If both 
handles are NULLHANDLE, then TRUE is returned.  Otherwise, FALSE is returned.
**Parameters :**
Input :
hSrc1Table  -  Handle to the first of two ID Tables that will be compared.

hSrc2Table  -  Handle to the second of two ID Tables that will be compared.

Output :
(routine)  -  TRUE if the two ID Tables contain the same contents, FALSE otherwise.


**See Also :**
[IDCreateTable](D:/md_files/IDCreateTable.md)
[IDTableIntersect](D:/md_files/IDTableIntersect.md)
[IDDeleteTable](D:/md_files/IDDeleteTable.md)
[IDInsertTable](D:/md_files/IDInsertTable.md)
---
