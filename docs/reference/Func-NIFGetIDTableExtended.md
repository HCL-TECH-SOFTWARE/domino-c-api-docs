##### Function : ID Table
##### NIFGetIDTableExtended - Add all notes of given collection into an ID Table
---
##### #include <nif.h>
STATUS **NIFGetIDTableExtended(**

	HCOLLECTION  hCollection,
	WORD  Navigator,
	DWORD  Flags,
	DHANDLE  hIDTable);
**Description :**
Add all notes of given collection into an ID Table. This routine cannot be  
used in application that are order dependent since the notes in ID table is 
completely unordered. The ID table can be  passed in non-empty if  the user 
wants to merge an existing table with collection note IDs
**Parameters :**
Input :
hCollection  -  collection to skim note ID's from

Navigator  -  NIF Read Entries read mask

Flags  -  NIF_GETIDTABLE_NOFILTER, NIF_GETIDTABLE_RESPONSES_TOO

hIDTable  -  ID Table to be filled with note id od this collection.

Output :
(routine)  -  (routine) - error status
NOERROR
ERR_XXX


**Sample Usage :**
```
STATUS far PASCAL NIFGetIDTable (HCOLLECTION hCollection,
	       WORD Navigator,
	       DHANDLE hIDTable)
	{
	return(NIFGetIDTableExtended(hCollection, Navigator, 0L, hIDTable));
	}
```
**See Also :**
[](D:/md_files/.md)
---
