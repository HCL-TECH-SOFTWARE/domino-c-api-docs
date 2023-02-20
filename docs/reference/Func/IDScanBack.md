##### Function : ID Table
##### IDScanBack - Scan the ID table for the last or previous entry.
---
```
#include <idtable.h>
BOOL IDScanBack(

	DHANDLE  hTable,
	BOOL  fLast,
	DWORD *retID);
```
**Description :**

Scan the ID table for the last or previous entry. The table itself must NOT be 
modified between iterations to this routine.  Also, user should ONLY call this 
routine with IDs that have previously been returned by this routine, NOT any 
old random number (except on first iteration).

**Parameters :**
Input :
hTable  -  handle of the table

fLast  -  TRUE if you want the last entry, FALSE if you want the previous entry

retID  -  Current ID (fLast = false)

Output :
(routine)  -  FALSE if no previous entry, TRUE if ID was returned


retID  -  address of the returned ID  (fLast = true)


**Sample Usage :**
```
	/* assumes hIDTable, a handle for an active IDTable with NoteIDs stored 
in it */

	BOOL bLast = TRUE;
	NOTEID NoteID = 0;  /* is overwritten via bLast == TRUE */


	while (IDScanBack( hIDTable, bLast, &NoteID))
	{
	 bLast = FALSE;
	 
	 /* Process NoteID */

	 ...
	}

}
```
**See Also :**
---
