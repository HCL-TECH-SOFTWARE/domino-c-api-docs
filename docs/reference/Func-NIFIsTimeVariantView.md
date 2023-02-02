##### Function : Views
##### NIFIsTimeVariantView - Check whether a view is a time variant view.
---
##### #include <nif.h>
BOOL **NIFIsTimeVariantView(**

	HCOLLECTION  hCollection);
**Description :**
Checks whether the view is a time-varying view or any type of view that is 
rebuilt on each open, for example, a soft deleted view. 
**Parameters :**
Input :
hCollection  -  Per-user colletion context handle.

Output :
(routine)  -  TRUE if the given view is timevariant view, one that must be rebuilt each time it is opened.


**Sample Usage :**
```
	/* Presumes hCollection, a COLLECTIONHANDLE for an open view and 
NoteID, its design note NOTEID */

	if ( NIFIsTimeVariantView(hCollection) )
	{
	 xprintf("We have a time variant view for NoteID %x\n",  NoteID);
	}
```
**See Also :**
[](D:/md_files/.md)
---
