##### Function : Note
##### NSFNoteUpdateExtended - Write in-memory note to on-disk database.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteUpdateExtended(

	NOTEHANDLE  hNote,
	DWORD  UpdateFlags);
```
**Description :**

This function writes the in-memory version of a note to its database.  Prior to 
issuing this call, a new note (or changes to a note) are not a part of the 
on-disk database.  This function allows using extended 32-bit DWORD update 
options, as described in the entry UPDATE_xxx.

You should also consider updating the collections associated with other Views 
in a database via the function NIFOpenCollection or NIFUpdateCollection, if you 
have added and/or deleted a substantial number of documents.  If the Server's 
Indexer Task does not rebuild the collections associated with the database's 
Views,  the first user to access a View in the modified database might 
experience an inordinant delay, while the collection is rebuilt by the Notes 
Workstation (locally) or Server Application (remotely).

**Parameters :**
Input :
hNote  -  Handle of note to write to database.

UpdateFlags  -  Flags that control the manner in which the note update is done. The flags are defined in UPDATE_xxx and may be ORed together.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_DATA_ONLY
ERR_UPDATE_CLASS
ERR_VERSION
ERR_CONFLICT
ERR_NOT_AUTHOR
ERR_NEW_NAME_KEY

ERR_SUMMARY_TOO_BIG -  "Field is too large (32K) or field's column in selection formula is too large".  You have appended more than about 16184 bytes to this note in items that have the ITEM_SUMMARY flag set. API functions such as NSFItemSetText set the ITEM_SUMMARY flag by default. Work around this problem by using NSFItemAppend to append some of these fields to the note without setting the ITEM_SUMMARY flag in the item_flags argument to NSFItemAppend. 



**See Also :**
[ITEM_xxx](/domino-c-api-docs/reference/Symb/ITEM_xxx)
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NIFUpdateCollection](/domino-c-api-docs/reference/Func/NIFUpdateCollection)
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[UPDATE_xxx](/domino-c-api-docs/reference/Symb/UPDATE_xxx)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
---
