##### Function : Views
##### NIFUpdateCollection - Update a collection.
---
```
#include <nif.h>
STATUS LNPUBLIC NIFUpdateCollection(

	HCOLLECTION  hCollection);
```
**Description :**

This function updates an open collection.  If the collection is out of date 
with respect to a database (if it was updated recently via NSFNoteUpdate), this 
routine can be called to perform a partial search of the database for all notes 
modified since the last time the collection was updated, and all notes found in 
the search are then added to the collection.  You should update a collection 
when you have finished adding and/or deleting documents that you might 
subsequently wish to recognize in that collection.

A collection may not be automatically updated when it is closed and then 
reopened. This will happen when concurrent applications are modifying databases 
in which the views and documents are in separate databases.

When a collection is updated, the positions of documents in the collection may 
change.  Any collection positions that have been obtained may no longer be 
correct.  The collection positions for these notes should be updated by calling 
NIFLocateNote.

**Parameters :**
Input :
hCollection  -  The handle of the collection you want to update.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is:

NOERROR - Collection successfully updated .
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NIFCloseCollection](/domino-c-api-docs/reference/Func/NIFCloseCollection)
[NIFLocateNote](/domino-c-api-docs/reference/Func/NIFLocateNote)
---
