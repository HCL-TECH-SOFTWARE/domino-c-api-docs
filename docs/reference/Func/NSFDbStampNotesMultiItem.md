##### Function : Database
##### NSFDbStampNotesMultiItem - Set same item value for every note in ID Table.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbStampNotesMultiItem(

	DBHANDLE  hDB,
	DHANDLE  hTable,
	DHANDLE  hInNote);
```
**Description :**

This function takes the  item values in the given note and stores (stamps) them 
in all the notes specified by an ID Table.  It overwrites the current item 
values, thereby updating the last modified time/date of each Note processed.  
If the item does not exist or is of a different data type, 
NSFDbStampNotesMultiItem() will create/delete the item and append the new value 
as required.

If you do not have the proper access to modify any one of the notes in the ID 
Table, ERR_NOACCESS will be returned.  Only those documents you are able to 
modify have been stamped.

**Parameters :**
Input :
hDB  -  A handle to a Domino database.

hTable  -  A handle to an ID Table.

hInNote  -  Handle of note containing specified item values to stamp to the set of notes contained in the table.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully stamped the notes contained in the ID Table.

ERR_DIRECTORY - This function is inappropriate for directories.

ERR_NO_STAMPED_NOTES - No documents were categorized(stamped).  

ERR_NOACCESS - You are not authorized to modify one or more of the documents specified.  Only those documents you are authorized to modify have been stamped.

ERR_xxx - Errors returned by lower level Notes functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[NSFDbGetModifiedNoteTable](/reference/Func/NSFDbGetModifiedNoteTable)
[NIFOpenCollection](/reference/Func/NIFOpenCollection)
---
