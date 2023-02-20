##### Function : Views
##### NIFOpenCollectionWithUserNameList - Access a collection of notes using a user name list.
---
```
#include <nif.h>
STATUS LNPUBLIC NIFOpenCollectionWithUserNameList(

	DBHANDLE  hViewDB,
	DBHANDLE  hDataDB,
	NOTEID  ViewNoteID,
	WORD  OpenFlags,
	DHANDLE  hUnreadList,
	HCOLLECTION far *rethCollection,
	NOTEHANDLE far *rethViewNote,
	UNID far *retViewUNID,
	DHANDLE far *rethCollapsedList,
	DHANDLE far *rethSelectedList,
	DHANDLE  nameList);
```
**Description :**

This function opens a collection of notes and allows for a NAMES_LIST structure 
UserName to provide authentication for trusted servers. It yields a collection 
handle. To access the collection, pass the collection handle as input to NIF 
functions like NIFReadEntries. Close the collection when finished accessing it 
using NIFCloseCollection;  this will free the memory associated with the 
collection.

A collection is a representation of a view or folder at one point in time. It 
consists of a filtered and sorted set of entries, where each entry corresponds 
to a document in the database or a category in the view or folder. 
NIFOpenCollection uses the view or folder definition and the state of the 
database to create or update the collection.

A collection is created the first time the view is opened by indexing all 
documents in the database that match the view selection criteria for views.  
Documents in folders are also indexed.  Collections are saved in the database 
file on disk so that opening an existing collection is very fast if the 
database has been minimally modified.  If the on-disk collection is out of date 
with respect to the notes in the database, generally, NIFOpenCollection will 
automatically perform a partial search of the database for all notes created or 
modified since the last time the collection was updated. It updates the 
collection with entries for the new or modified notes before returning to the 
caller.

Use NIFReadEntries after opening the collection to get information about the 
notes in the collection. The collection does not reflect documents created or 
modified after the collection was opened. Use NIFUpdateCollection to update an 
open collection.  Also use NIFUpdateCollection if the SignalFlag returned by 
NIFReadEntries indicates that the collection should be updated.  In this case, 
NIFReadEntries will need to be called again to obtain the updated collection 
information.

NIFOpenCollection can also return other information about the view or folder 
and the database at the same time it opens the collection. See arguments 5, 7, 
8, 9, and 10.

NOTE: The behavior described above is the default behavior for this function. 
The behavior may be modified by setting one or more of the flags in the 4th 
parameter.

NOTE: If there are concurrent applications updating the same databases, then 
the collection may not be automatically updated when it is reopened.  This will 
happen when the views and documents are in separate databases.

NOTE: Only the following configurations are supported by NIFOpenCollection for 
views:  the hDataDB argument references the same database as the hViewDB 
argument, or the hViewDB argument references a LOCAL database, and the hDataDB 
argument references a remote database.  For folders, the hDataDB argument must 
reference the same database as the hViewDB argument.



**Parameters :**
Input :
hViewDB  -  The handle of the database that contains the view or folder.

hDataDB  -  The handle of the database that contains the data notes.  For folders this must reference the same database as hViewDB.

ViewNoteID  -  The ID of the view or folder note in the database. Use NIFFindView to obtain the note ID of a view or folder note given its name.

Note: The value (NOTE_CLASS_DESIGN | NOTE_ID_SPECIAL) may be specified in the ViewNoteID parameter of NIFOpenCollection to open the design collection of the database. The design collection is a collection of all the design notes in the database, including forms, views, folders, fields, macros, and replication formulas.

OpenFlags  -  Flags that control the manner in which the collection is created. The flags are defined in OPEN_xxx (collection), and may be bitwise or'ed together to combine functionality.

hUnreadList  -  A handle to an ID Table specifying a list of unread documents. Set to NULLHANDLE if you are not managing an unread list. Otherwise, if your program maintains its own unread list, the ID Table must be your program's list of unread note IDs, including the time/date when the list was last updated. NIFOpenCollection will update the list and the time/date to reflect new and modified documents in the database. 

Note 1: If the ID Table is initially empty, or if the TIMEDATE specified on input is zero, NIFOpenCollection populates the ID Table with the IDs of all unread documents in the database.

Note 2: See NSFDbGetUnreadNoteTable and NSFDbSetUnreadNoteTable for information on accessing a user's unread list.

Note 3:  NIFOpenCollection will update the ID Table with any notes created or modified in the database since the time/date in the ID Table regardless of whether the notes appear in the collection being opened or not.

Note 4: ID Tables store notes in the order of the Note ID, not the order in which they appear in the view or folder.

nameList  -  May be NULLHANDLE or a HANDLE to a NAMES_LIST structure that contains a UserName that is used to provide authentication for trusted servers.  This causes the UserName's ACL permissions in the database to be enforced.  Please see NSFBuildNamesList for more information on building a NAMES_LIST structure.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOTE_DELETED
ERR_VIEW_NOACCESS
ERR_ITEM_NOT_FOUND
ERR_COLLECTION_NOT_CREATED


hUnreadList  -  If you specify a handle, NIFOpenCollection updates the list of IDs and the "Time" field in the ID table. NIFOpenCollection adds IDs to the list for all documents created or modified in the database since the time/date specified in the Time field. It also removes IDs from the list for all documents that were deleted from the database since that Time. 

Note1: If the ID Table is initially empty, or if the TIMEDATE specified on input is zero, NIFOpenCollection populates the ID Table with the IDs of all unread documents in the database.

Note 2:  NIFOpenCollection will update the ID Table with any notes created or modified in the database since the time/date in the ID Table regardless of whether the notes appear in the collection being opened or not.


rethCollection  -  The address of an HCOLLECTION variable in which the handle of the collection is returned.

rethViewNote  -  Reserved for internal use.  This must be specified as NULL.

retViewUNID  -  A pointer to a UNID that will receive the universal note ID of this view or folder. This ID is not necessary for obtaining the collection. Set the argument to NULL if you don't want this return.

rethCollapsedList  -  The address of a HANDLE variable in which the handle of the expanded/collapsed note ID Table is returned. This table is not necessary for obtaining the collection. Set the argument to NULL if you don't want this return.

The caller is not responsible for freeing this ID Table. The ID Table is freed when NIFCloseCollection is called.

rethSelectedList  -  The address of a HANDLE variable in which the handle of the selected note ID Table is returned. This table is not necessary for obtaining the collection. Set the argument to NULL if you don't want this return.

The caller is not responsible for freeing this ID Table. The ID Table is freed when NIFCloseCollection is called.


**See Also :**
[IDCreateTable](/reference/Func/IDCreateTable)
[NIFCloseCollection](/reference/Func/NIFCloseCollection)
[NIFOpenCollection](/reference/Func/NIFOpenCollection)
[NIFReadEntries](/reference/Func/NIFReadEntries)
[NSFDbGetUnreadNoteTable](/reference/Func/NSFDbGetUnreadNoteTable)
[NSFDbSetUnreadNoteTable](/reference/Func/NSFDbSetUnreadNoteTable)
[OPEN_xxx (collection)](/reference/Symb/OPEN_xxx (collection))
---
