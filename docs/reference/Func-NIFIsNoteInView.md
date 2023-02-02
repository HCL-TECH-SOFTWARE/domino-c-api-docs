##### Function : ID Table
##### NIFIsNoteInView - Check whether a note ID is in a given view.
---
##### #include <nif.h>
STATUS **NIFIsNoteInView(**

	HCOLLECTION  hCollection,
	NOTEID  NoteID,
	BOOL *retInView);
**Description :**
Check whether a note ID is in a given view and whether the caller has the 
privileges to see it. If there is an ID table for the collection and the note 
is not in the table, then the note is not in the view. If  there is no ID table 
for the collection or if access to a note needs to be checked, then this 
routine checks a note by looking it up in the note ID index.  
**Parameters :**
Input :
hCollection  -  Handle of per user collection context

NoteID  -  NoteID being tested

Output :
(routine)  -  Error status
NOERROR - if success
ERR_XXX - Error ID if fails


retInView  -  Place to receive boolean indicator if note is in view.

**Sample Usage :**
```
BOOL Filter(DWORD noteid, STATUS *retErr)
{
	BOOL disqualify=FALSE;
	BOOL bInView;
	
	const STATUS error = NIFIsNoteInView(hColl, noteid, &bInView);
	if (error != NOERROR)
	{
	 if (retErr != NULL)
	  *retErr = err;

	 xprintf("NIFIsNoteInView failed [%e] for NoteID %d", err, noteid);
	 return FALSE;
	}
	
	return bInView;
}
```
**See Also :**
[](D:/md_files/.md)
---
