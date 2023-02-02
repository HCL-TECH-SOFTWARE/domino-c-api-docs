##### Function : index
##### NIFUpdateFilters - Check whether a collection that is open on a remote server is up-to-date.
---
##### #include <nif.h>
STATUS **NIFUpdateFilters(**

	HCOLLECTION  hCollection,
	WORD  ModifyFlags);
**Description :**
Check whether a collection that is open on a remote server is up-to-date. Call 
this routine when making changes to any IDTable index filter (unread list, 
expand/collapse list, selected list). 

No handles to the IDTables are required as input since they were established 
via NIFOpenCollection. 

If the collection is open on a remote server, then the IDTable lists are 
re-sent to the server. If the collection is "local", then the call has no 
effect.
**Parameters :**
Input :
hCollection  -  Per user collection context.

ModifyFlags  -  Flags indicating which IDTables were modfied as described in FILTER_XXX.

Output :
(routine)  -  Returns status from the call, either success or an error. The return codes include: 
NOERROR - Successfully updated the NIF filter. 
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.). There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**Sample Usage :**
```
	DHANDLE hUnreadList; 
	STATUS error; 

	if (error = IDCreateTable(0, &hUnreadList)) 
	 return error; 

	if (error = NIFOpenCollection( 
	 db_handle, /* Handle of db with view. */ 
	 db_handle, /* Handle of db with data. */ 
	 ViewID, /* Note id of the view. */ 
	 0, /* Collection open flags. */ 
	 hUnreadList, /* Handle to unread ID list (input and return). */ 
	 &hCollection, /* Collection handle (return). */ 
	 NULLHANDLE, /* Handle to open view note (return). */ 
	 NULL, /* Universal note id of view (return). */ 
	 NULLHANDLE, /* Handle to collapsed list (return). */ 
	 NULLHANDLE)) /* Handle to selected list (return). */ 
	{ 
	 NSFDbClose (db_handle); 
	 PrintAPIError (error); 
	 NotesTerm(); 
	 return (1); 
	} 
	IDInsertRange(hUnreadList, 40, 80, FALSE); //Adding entries into table. 
	if(error = NIFUpdateFilters(hCollection, FILTER_UNREAD)) 
	{ 
	 NIFCloseCollection(hCollection); 
	 PrintAPIError (error); 
	 return 1; 
	} 
```
**See Also :**
[](D:/md_files/.md)
---
