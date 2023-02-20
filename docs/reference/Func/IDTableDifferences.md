##### Function : ID Table
##### IDTableDifferences - Determine the changes to make to table 1 same as table 2
---
```
#include <idtable.h>
STATUS IDTableDifferences(

	DHANDLE  hSrc1Table,
	DHANDLE  hSrc2Table,
	DHANDLE *rethAdds,
	DHANDLE *rethDelete,
	DHANDLE  rethSame);
```
**Description :**

Determine the changes to make to table 1 same as table 2. table 1 is the 
original table, and table 2   needs modification. This is just an optimized 
version of doing intersections and deletions. this routine checks for overlap 
and ensures the ranges are aligned. If the resulting table is null after the 
equation indicates  there is no difference. table will be locked during the 
routine execution to avoid accidental alteration 

**Parameters :**
Input :
hSrc1Table  -  source table 1

hSrc2Table  -  source table 2

Output :
(routine)  -  Routine return status from this call. Either success or whatever the error is.


rethAdds  -  handle of the add table (if addition is determined)

rethDelete  -  handle of deletion table (if deletion is determined)

rethSame  -  handle of the same table 


**Sample Usage :**
```
	/* Assumes hEntryIDTable and hNewIdTable, populated IDTables */

	DHANDLE hDeleted = NULLHANDLE;

	{
	 error = IDTableDifferences(hEntryIdTable, hNewIdTable,
	    NULL,
	    &hDeleted,
	    NULL);

	  IDDestroyTable(s_hEntryIdTable);
	  s_hEntryIdTable = s_hNewIdTable;
	  s_hNewIdTable = NULLHANDLE;
	 }

	 /* Process documents found to be deleted */
	 if ( NOERROR == error )
	 {
	  NOTEID NoteId;
	  BOOL bFirst = TRUE;
	  while( IDScan(hDeleted, bFirst, &NoteId))
	  {
	   bFirst = FALSE;
	   ProcessThisNote(NoteId);
	  }
	 }
	}

	if ( hDeleted )
	 IDDestroyTable(hDeleted);

	return error;
}
```
**See Also :**
---
